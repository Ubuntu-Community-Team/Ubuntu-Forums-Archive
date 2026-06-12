---
title: "greasemonkey to chrome userscripts"
date: 2009-11-19
forum: Programming Talk
---

### Post by slavik on 2009-11-19
Anyone have any guides on how to convert greasemonkey scripts to chrome userscripts?

I am having trouble with one of my scripts editing a text input in a form. I am referencing it via id.

---

### Post by Reiger on 2009-11-20
<input type="text"/> has a quirk: while often <input type="text">Value</input> appears to work; that should be actually <input type="text" value="Value"/>.

So you may see unexpected results if the HTML/JS code is cutting corners there: try checking input.value as well as inpunt.innerHMTL; with input = document.getElementById('whateverYourID').

---

