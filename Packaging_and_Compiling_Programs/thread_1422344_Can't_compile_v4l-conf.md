---
title: "Can't compile v4l-conf"
date: 2010-03-05
forum: Packaging and Compiling Programs
---

### Post by BeardedChimp on 2010-03-05
Hey,

I have quite a lot of experience of compiling etc. but this one has me flumexed. I'm running karmic 64bit.

I usually compile from svn, but I specifically want the ubuntu source for this package as I'm diagnosing a bug in v4l-info

So I obtained the source through apt-get source v4l-conf
Ran apt-get build-dep v4l-conf

Enter the directory xawtv-3.95.dfsg.1
./configure
No problems
make
It can't find some header file, look on the internet and Its in some X11 fonts folder. I copy it across and run again and get this error:

console/fbtools.c:24:22: error: asm/page.h: No such file or directory

Looking on the net it seems this is something to do with old kernel headers, but since this is from the karmic source repositories surely the source is patched to fix it, otherwise how else does the package maintainer compile it?

Is is something to do with the .diff file that apt-get source downloads because I tried all kinds of patching with it and I can't work out to do it if that is the case.

Cheers for any help.

---

### Post by mc4man on 2010-03-05
look at the 07_page_size.dpatch which removes that include (among other things
> -#include <asm/page.h>

---

