---
title: "Library for creating PostScript?"
date: 2010-10-31
forum: Programming Talk
---

### Post by Colin@oxford on 2010-10-31
I was wondering whether there was a library available for generating PostScript (or any other formatted document files) from C/C++.  I ask because I am looking at some code that is creating PS files and it appears to be doing it all itself.  Surely there must be a library somewhere that can handle the vagaries of the syntax and fiddly things like kerning and line breaks while leaving the programmer to concentrate on the text that needs to go into the document.  I was wondering whether I could enhance the output options to PDF etc., but if I have to do it all from scratch this seems rather tedious.

---

### Post by dv3500ea on 2010-10-31
[pslib]("http://pslib.sourceforge.net/")

To use it in your programs install [pslib-dev]("apt:pslib-dev")

---

### Post by Colin@oxford on 2010-11-01
Thanks - just what I was looking for.  Expecting it to be "libps" didn't help in the search :-(

---

### Post by Colin@oxford on 2010-11-01
How do I determine which fonts are availble for pslib?

---

