---
title: "How 64 bit differs on Linux and windows"
date: 2010-05-15
forum: Programming Talk
---

### Post by jacensolo on 2010-05-15
This is a seemingly simple question that I seem to be unable to find the answer to. On my Arch Linux 64 bit install I have to install the 32  bit libraries to get some 32 bit programs working (not sure if statically linked programs work though). This kind of makes since. However, on Windows 32 bit applications install on 64 bit installations with no problem. Is this because most windows programs are statically linked?

---

### Post by JwB Zoofware on 2010-05-15
I believe there's a subsystem called WoW64 in Windows for maintaining 32bit compatability.

[http://en.wikipedia.org/wiki/WoW64](http://en.wikipedia.org/wiki/WoW64)

---

### Post by Ferrat on 2010-05-15
Windows maintains 32bit compability just like Linux with extra files etc but the difference is that in Linux you have to option not to use it :P

---

### Post by Cracauer on 2010-05-15
Windows just always (exceptions apply) ships a 32 bit version of a shared library along with the 64 bit version. Presumably both are compatible with the same header file, too.

In Linux that is partially done by Fedora, but not on a large scale.

Debian/Ubuntu are particularly ignorant here. In their defense, always providing 64 and 32 bit versions would be a hassle due to the crosscompiling requirement.

---

