---
title: "Compiling the Kernel and CFLAGS"
date: 2010-09-21
forum: Packaging and Compiling Programs
---

### Post by Super Nade on 2010-09-21
Guys,

First up, I am a total noob. Never compiled anything from scratch in Ubuntu. Used Gentoo for a bit (relying on my l337 Google skills to fix problems), but not seriously.

I finished just compiling my kernel (took about 5 bloody hours) today. Is there any way I can set custom CFLAGS like it is shown in the Gentoo Handbook i.e is there a global /etc/make.conf file I can edit?
I want to compile the latest and greatest kernel from kernel.org.

Finally, is there a kernel specific benchmark to see if recompiling the kernel was worth my time?

Thanks!

---

### Post by Super Nade on 2010-09-25
O.k, I did a lot of digging around and did the following.

1. Downloaded the latest kernel from kernel.org.
2. Extracted the files to a new folder named /src in the home folder.
3. Edited the "Makefile" with the following options:
```
# SHELL used by kbuild
CONFIG_SHELL := $(shell if [ -x "$$BASH" ]; then echo $$BASH; \
	  else if [ -x /bin/bash ]; then echo /bin/bash; \
	  else echo sh; fi ; fi)

HOSTCC       = gcc
HOSTCXX      = g++
HOSTCFLAGS   = -Wall -Wmissing-prototypes -Wstrict-prototypes -O3 -fomit-frame-pointer -pipe -march=pentium-m
HOSTCXXFLAGS = "${CFLAGS}"
```

There are other instances of CFLAGS in the Makefile, but I think these are Global options. Need to read more though. Perhaps one of the experts here can point me in the right direction? I am willing to read,all I need is a link or a pointer on what to read?

I followed this procedure to compile the kernel--->
[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

---

