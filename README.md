# IMG-auto-generera-lazy-loading-alt-text
Hämtar alla &lt;img> inom DOM och applicerar lazy loading och saknas alt-text används bildens namn.

## JS kod

```javascript
function optimeraBilder(container = document) {
const bilder = container.querySelectorAll('img');
bilder.forEach(img => {
if (!img.hasAttribute('loading')) {
img.setAttribute('loading', 'lazy');
}
if (!img.getAttribute('alt') || img.getAttribute('alt').trim() === "") {
const src = img.getAttribute('src');
if (src) {
let filnamn = src.split('/').pop().split('.')[0];
let snyggAlt = filnamn.replace(/[-_]/g, ' ');
snyggAlt = snyggAlt.charAt(0).toUpperCase() + snyggAlt.slice(1);
img.setAttribute('alt', snyggAlt);
}}});
}
document.addEventListener('DOMContentLoaded', () => optimeraBilder());
```

Har du frågor, skicka mejl till projektnano.xyz@proton.me
