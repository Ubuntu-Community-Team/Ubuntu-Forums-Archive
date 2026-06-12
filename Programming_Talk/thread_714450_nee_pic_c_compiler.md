---
title: "nee pic c compiler"
date: 2008-03-03
forum: Programming Talk
---

### Post by @vijay@ on 2008-03-03
im looking for a good pic c compiler ; that will be able to support 18F series 
there are many for windows , but im unable to find any good ones for linux
i have seen picc for hi-tech , but its very costly i prefer a free one :)

thanx in advance

---

### Post by fedex1993 on 2008-03-03
there is gcc i use that for compiling C programs 
sudo apt-get install build-essentials i think it is once you install it type man gcc

---

### Post by geraldm on 2008-03-03
sdcc is GPL-2.0 (LPGL by file), and free.  It may take a bit of an effort to become familiar with using it.  The pic18F* files are more clearly indicated in SRCTOPDIR/device/include/pic16/ directory.  They are experimental, and incomplete, but there are quite a few chips already in there.
[http://sdcc.sourceforge.net](http://sdcc.sourceforge.net)

Gerald

---

### Post by @vijay@ on 2008-03-05
thanx sdcc
whr can i get good examples for sdcc ; 
if i have a c code written in different compiler say mikroc ; does sdcc compile it?

---

### Post by geraldm on 2008-03-06
You might find some answers in the mailing list on sourceforge
[https://sourceforge.net/forum/forum.php?forum_id=1864&et=0](https://sourceforge.net/forum/forum.php?forum_id=1864&et=0)
That would be the best place to answer questions about sdcc.

I doubt there is a good comparison for C compilers.  Try it and see.

Gerald

---

### Post by KaeseEs on 2008-03-06
I was in a similar boat about 2 months ago, as I was looking for a Linux-based C compiler that targeted the 8051 family (I had been using the crappy trial Keil compiler in a W32 environment).  I found that SDCC works well, although you will likely have to alter header files that include non-ANSI C (register definitions &c.)

---

