---
title: "iframe"
date: 2009-05-26
forum: Programming Talk
---

### Post by sandyd on 2009-05-26
how do i make the page read the title of the page thats in the iframe and display it as the page title?

as in...

if the page being displayed by the iframe is "dog", i want the parent page that the iframe to have the title "dog"

---

### Post by Reiger on 2009-05-26
Rephrased: I want to transfer text content from the iframe element xyz to the title element; how do I modify the underlying document? Answer: look into modifying the DOM Tree of the underlying document with for instance a bit of JavaScript.

---

### Post by DocForbin on 2009-05-26
Untested, but in the iframe onload you should be able to use parent.document.title = document.title (assuming they are on the same domain). Or from the parent you could use document.title = frames['myframe'].document.title.

hth

---

