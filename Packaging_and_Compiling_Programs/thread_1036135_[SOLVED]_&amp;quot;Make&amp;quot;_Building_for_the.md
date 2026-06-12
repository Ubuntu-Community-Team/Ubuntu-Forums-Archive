---
title: "[SOLVED] &amp;quot;Make&amp;quot; Building for the Wrong Kernel"
date: 2009-01-10
forum: Packaging and Compiling Programs
---

### Post by mysticrider92 on 2009-01-10
Ok, I am trying to install a PS3 Eye on Ubuntu AMD64. The driver for this is in a special Video 4 Linux that I have to compile (what fun.. :-?). 

I just built a custom kernel, version 2.6.27-2. The Makefile for the V4L is trying to find a module .config in /lib/modules/2.6.27-server/build, however, it should be building with /lib/modules/2.6.27.2-4x1/build. How do I tell make to look here for the .config file? It isn't set in this particular Makefile, and since Ubuntu doesn't use a make.conf, I can't set it that way.

Thanks in advance.

---

### Post by mysticrider92 on 2009-01-11
I found out that make wasn't the problem here, seems like the program itself was looking for the wrong config file. It is working fine now, with a different version of the patched V4L.

---

