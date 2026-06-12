---
title: "Which compiler i used"
date: 2008-01-08
forum: Packaging and Compiling Programs
---

### Post by oubountou on 2008-01-08
Hi all,

i have two compilers on my machine: gcc and cc (sun studio)
i have a compiled file. is there a way to see which compiler i have used to compile it?

Thanks in advance.

---

### Post by stroyan on 2008-01-09
Try using readelf or objdump to dump the .comment section like this- ```
readelf -x .comment a.out
objdump -s -j .comment foo.o
```At least recent versions of gcc write their version information in that section.  (But the section may be stripped out by the build of your compiled file.)

---

### Post by oubountou on 2008-01-09
The second one worked great..
many Thanks!!

---

