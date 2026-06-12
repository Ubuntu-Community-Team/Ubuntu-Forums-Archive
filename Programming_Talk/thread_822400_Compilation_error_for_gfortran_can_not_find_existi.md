---
title: "Compilation error for gfortran: can not find existing file"
date: 2008-06-08
forum: Programming Talk
---

### Post by Misha__ on 2008-06-08
It looks like a bad joke:

```
$ gfortran   -c -g3 -O0  TB_par.f90
TB_par.f90:49.11:

   USE HDF5
          1
Fatal Error: Can't open module file 'hdf5.mod' for reading at (1): No such file or directory

$ ls /usr/local/include/ | grep hdf5
hdf5.h
hdf5_hl.h
hdf5.mod

```
N.B. Setting INCLUDE does not help. vim /usr/local/include/hdf5.mod works, thus it is not a permission problem. 

Is it some kind of bug? I did similar thing many times. 

Actually, it looks like gcc bug. Intel compiler sees this file. However, due to incompatibility of gcc 4.2 with intel 10.1 I compiled library with gfortran and thus can not link it from intel.

P.S. Actually, -I/usr/local/include/ works. However, I am extremly surprised by this (nonstandard, in my opinion) gcc behaviour.

---

### Post by KingTermite on 2008-06-09
I'm still learning the gcc setup and architecture (haven't used it since college, and then only in "normal" situations).

Sounds like the standard search path for header files is not including the /usr/local/include path, which, based on your surprise, I assume should be the standard place for them.

Is there an environment variable which sets this path that has been screwed up perhaps?

---

