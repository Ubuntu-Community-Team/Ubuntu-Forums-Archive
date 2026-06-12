---
title: "javascript query"
date: 2010-02-22
forum: Programming Talk
---

### Post by maclenin on 2010-02-22
Is it possible to use document.getElementById() to dynamically modify the "target value" of onmouseover - in the same way that I might modify an "src" or "href" target?

Example:

old (html) value: onmouseover="some_function()"

js: document.getElementById("test").onmouseover="some_other_function()";

new (html) value: onmouseover="some_other_function()"

Thanks for any guidance.

---

### Post by meastwood on 2010-02-22
it's pretty straight forward to do if you use jquery.  There are several functions that will do the job e.g. $('tag_id').mouseover(function_to_run);,
$('tag_id').live('mouseover', function_to_run);

function_to_run can be predefined or anonymous.

If it can be done using jquery lib then you can do it the old way using 'pure' javascript.  $('tag_id') is basically a 'wrapper' that uses 'document.getElementById' and/or 'document.getElementsByTagName' however the jquery function/'wrapper' does a lot more - saving on a lot of coding and is usually cross-browser compatible which saves a lot on coding and headaches.

---

