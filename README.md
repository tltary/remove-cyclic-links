# Remove cyclic links JS

Takes all links from the page and replaces with span to avoid seo looping.

[Demo](https://tltary.github.io/remove-cyclic-links/index.html)

```js
let link = document.querySelectorAll('a');
let url  = window.location.href;
for (let i = 0;i < link.length;i = i + 1) {
	if (url == link[i].href) {
		replaceTag(link[i]);
	}
}
function replaceTag(element)
{
    let elementNew = document.createElement('span');
    elementNew.innerHTML = element.innerHTML;
    Array.prototype.forEach.call(element.attributes, function(attr) {
        elementNew.setAttribute(attr.name, attr.value);
    });
    element.parentNode.insertBefore(elementNew, element);
    element.parentNode.removeChild(element);
    return elementNew;
}
```