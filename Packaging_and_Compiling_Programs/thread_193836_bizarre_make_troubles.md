---
title: "bizarre make troubles"
date: 2006-06-10
forum: Packaging and Compiling Programs
---

### Post by pinegreen on 2006-06-10
Hi,

I hope that this is the right forum. I develop a lot of numerical code, mostly fortran. Since, I want to compile it on various machines, I commonly used the following type of construct in Makefile:


ifeq ($(HOST),feynman)
LAPACKL = -L/home/slosar/work/mkl/8.1/lib/32  -lmkl_lapack -lmkl_ia32 -lguide -lm -lpthread
CPPLINK = -L/usr/lib /usr/lib/libstdc++.so.6.0.3  /usr/lib/gcc/i386-redhat-linux/3.4.5/libgcc_s.so
endif
ifeq ($(HOSTNAME),pavla)
LAPACKL = -L/opt/intel/mk
....etc etc

This seems to work everywhere (for ages), except on my newest ubuntu DD machine, where it simply ignores all enviroment variables when I type make... They just don't go in, for example, if I put $(HOSTNAME) on any target, it is just empty even though echo $HOSTNAME spits something out on the command line... I am baffled and don't know how to even start debugging this.
Any ideas?

---

### Post by drl on 2006-06-10
Hi, pinegreen.

This might help ... cheers, drl
>        -e   Give  variables  taken from the environment precedence over vari-
            ables from makefiles.
- from the man page for GNU make

---

