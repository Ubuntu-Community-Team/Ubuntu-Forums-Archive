---
title: "Libexif and ImageMagick header/src issue"
date: 2009-08-28
forum: Packaging and Compiling Programs
---

### Post by paradigm2 on 2009-08-28
Hello I am trying to compile a program which has been modified and is supposed to work but isn't. When compiling I get this error when doing make:

**ISSUE SOLVED. I needed to add the proper libraries to the makefile**

I have libexif installed as well as ImageMagick in /usr/include though and have verified that at least the definitions are there. I have also checked to make sure that make is at least getting to the headers by modifying them and noting the difference.

But it's acting like it just can't find the proper definitions. Where are these definitions supposed to be located that it can't find them?  Any hints as what is going on.

---

### Post by paradigm2 on 2009-08-28
Solved

---

