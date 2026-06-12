---
title: "Having trouble installing software"
date: 2016-04-29
forum: New to Ubuntu
---

### Post by vic15 on 2016-04-29
Hi there,

I'm fairly new to Ubuntu and I'm trying to install a software called StoBe in my computer. 

Here is a link to the instructions that the developer provides:

[http://www.fhi-berlin.mpg.de/KHsoftware/StoBe/#Install](http://www.fhi-berlin.mpg.de/KHsoftware/StoBe/#Install)

I was able to complete Step 1 just fine. However, I do not see the Readme file and I have no idea on what the Makefile is. There is also supposed to be a $StoBe directory but I don't see that either.

I think I'm supposed to use a "make" command to get the Makefile, but I don't know how to actually use it.

Could someone be kind enough to guide me thorugh the process? It seems like a straightforward set of instructions but I'm not familiar enough with Ubuntu to get it done.

Thank you,

Vic

---

### Post by nothingspecial on 2016-04-29
Hi

Those are really rubbish instructions!! So guessing here

$StoBe is just what ever directory you downloaded and unpacked it into

make -f <makefile>  (<makefile> is the makefile you need, there are probably different ones depending on architecture etc)

It's not Readme but Readme.1st

---

