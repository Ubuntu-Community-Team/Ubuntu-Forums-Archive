---
title: "Compiling gcc-4.2: configure and __WORDSIZE"
date: 2007-02-27
forum: Programming Talk
---

### Post by Dr Eigen on 2007-02-27
Crossposted from the x86 64-bit Users forum:

I'm trying to build gcc-4.2 (I want the latest gfortran) on an amd64 box with 64 bit Ubuntu. In the middle of the build it borks when including gnu/stubs.h, as this tries to include gnu/stubs-32.h which doesn't exist. Looking at stubs.h, it seems gnu/stubs-64.h (which does exist) would be included were __WORDSIZE defined to be 64. I've tried playing with the lib/lib32/lib64 logic in gcc/config/i386/t-linux64, and --disable-multilibs, to no avail.

Any clues as to how to convince configure to set the appropriate defines to get a 64 bit gcc build?

---

### Post by Dr Eigen on 2007-03-01
After no useful help here, the x86_64 forum or gcc-help, I worked it out.

Solution was simple:  set CFLAGS to -m64 before configure.

Strange, as the previously installed gcc produced 64 bit execs by default.

---

