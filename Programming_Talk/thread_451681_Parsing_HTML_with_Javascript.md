---
title: "Parsing HTML with Javascript"
date: 2007-05-22
forum: Programming Talk
---

### Post by eightysix on 2007-05-22
I was wondering if there was a way to parse an HTML page with Javascript. I know about the "document.getElementById('foo')" function, but I want to parse the whole HTML document for text. I'm trying to parse the text in an HTML page and turn obfuscated text like "hxxp://.*" and "ttp://.*" into links. Thanks.

---

### Post by phossal on 2007-05-22
You can create or receive (as in an async req) document fragments. Then loop through the nodes. It seems like a project that would require something like that would use a language with a better api for such things as part of its delivery method.

---

### Post by eightysix on 2007-05-22
I'm trying to make a Greasemonkey extension for use on all webpages. I have the regex stuff under control, but I just don't know where to begin when it comes to the actual parsing of the data.

---

### Post by Mirrorball on 2007-05-22
The code has already been parsed by the browser and it's available as the DOM tree, which you can navigate through with Javascript.

---

### Post by barmazal on 2007-05-23
try advanced libraries of JS, there must be one that loops through DOM so you can access it's innerHTML or value in case you need it.

---

### Post by RedSquirrel on 2007-05-24
getElementsByTagName() is what you want. [EDIT: Or at least it might be; I just re-read your first post, and there are probably a few ways to do what you want.]

If you're not familiar with JavaScript and the DOM API, I suggest you pick up a reference book such as "JavaScript - The Definitive Guide - 5th edition" by David Flanagan. You can also look for tutorials on the web, but I feel a comprehensive book like this is better.

---

