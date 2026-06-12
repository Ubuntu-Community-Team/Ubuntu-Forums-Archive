---
title: "dealing with bad utf-8 characters xml/xslt"
date: 2010-06-29
forum: Programming Talk
---

### Post by badperson on 2010-06-29
I'm running an xslt stylesheet on some xml files, and the output files are coded correctly, but failing a validity check because they have bad-utf8 characters. 

It doesn't say what the character is or what to replace it with. Any ideas how to get that information? 

I was parsing with xerces.
bp

---

### Post by Some Penguin on 2010-06-29
The SAX parsers that I've seen will normally indicate the character and position.  If you're using a DOM parser, you might want to try SAX.

---

