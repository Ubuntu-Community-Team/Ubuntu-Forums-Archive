---
title: "Linking LAPACK and Fortran"
date: 2014-05-23
forum: Programming Talk
---

### Post by steamedxander on 2014-05-23
I am running 12.04 on a 64-bit machine and I am trying to compile a Fortran 90 program. I installed the LAPACK files through Synaptic but when I try to compile the program I am told "Fatal Error Can't find module file 'lapack.mod' for reading at (1): No such file or directory.

My original attempts include:
gfortran test.f90  -L/usr/lib/lapack -liblapack.a

The file locations are correct. I'm just happy to take whatever information you can offer.

---

### Post by steeldriver on 2014-05-23
DISCLAIMER: I don't really use fortran - I just have a perverse interest in this kind of thing

I don't think your error is related to linking the lapack library (at least not directly) - it's telling you that the test executable needs a **local module** called lapack.mod. Where did you get the test.f90 file from? is there also a lapack.f90 file? if so you would need to compile that as well, either as a separate step or something like

```

gfortran lapack.f90 test.f90 -llapack

```

See for example --> [http://www.cs.mtu.edu/~shene/COURSES/cs201/NOTES/chap06/mod-files.html](http://www.cs.mtu.edu/~shene/COURSES/cs201/NOTES/chap06/mod-files.html)

---

### Post by steamedxander on 2014-05-23
Upon downloading from Synaptic there is no lapack.f90 file. the test.f90 is just my own piece of code. 

I typed "whereis lapack.mod" and my output was the same as the directory I was using before so I'm a little baffled.

---

### Post by steeldriver on 2014-05-23
I'm confused - do you mean there *is* a lapack.mod file in your current directory? or in the /usr/lib/lapack directory? I can't find a reference to such a file in any of the system packages

---

### Post by steamedxander on 2014-05-23
I meant in the /usr/lib/lapack directory. Didn't mean to be so ambiguous.[ATTACH=CONFIG]253397[/ATTACH]

---

