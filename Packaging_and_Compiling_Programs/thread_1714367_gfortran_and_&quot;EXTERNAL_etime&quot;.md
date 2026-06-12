---
title: "gfortran and &quot;EXTERNAL etime&quot;"
date: 2011-03-25
forum: Packaging and Compiling Programs
---

### Post by grandmonstre on 2011-03-25
hello
 
i have problem after compiling with gfortran 95 all of files into object file. But it announced:
 
./obj/linux-gfortran-4.5/libcpu.o: In function `libcpu_':
libcpu.f:(.text+0x4e): [COLOR=red]undefined reference to `etime[/COLOR]_'
../obj/linux-gfortran-4.5/wrttim.o: In function `wrttim_':
wrttim.fpp:(.text+0x16): [COLOR=red]undefined reference to `etime_'
[/COLOR]collect2: ld returned 1 exit status
make: *** [ns2bat_linux-gfortran-4.5.v7.3] Error 1
 
 I think i haven't right version lapack with fortran 95, so i installed lapack 3.2.2 . But it still doesn't work. Can you help me ?

---

### Post by MadCow108 on 2011-03-25
I guess you need to fix your code:
[http://gcc.gnu.org/ml/fortran/2007-03/msg00305.html](http://gcc.gnu.org/ml/fortran/2007-03/msg00305.html)

---

### Post by grandmonstre on 2011-03-28
thanks , i changed my initial code from 
[COLOR=royalblue]external etime[/COLOR]
[COLOR=royalblue]real etime[/COLOR]
to:
[COLOR=royalblue]external real etime [/COLOR]
and it works :)

---

