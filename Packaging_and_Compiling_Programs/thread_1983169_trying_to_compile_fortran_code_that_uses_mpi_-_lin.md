---
title: "trying to compile fortran code that uses mpi - linking issues?"
date: 2012-05-19
forum: Packaging and Compiling Programs
---

### Post by brushman on 2012-05-19
Hi, I am trying to compile a fortran code which uses mpich2. I am using gfortran. Since originally I was getting the error

Error: Can't open included file 'mpif.h'

I have added -I/usr/lib/mpich2/include/ which has gotten rid of that error, and now I have errors such as these:

undefined reference to `mpi_send_'
undefined reference to `mpi_recv_'
.
.
.

As a side note I'm also getting a warning:

Warning: Blanket SAVE statement at (1) follows previous SAVE statement

But I'm guessing that is unrelated to my undefined reference problem.

Does anyone know how to fix this?

Thanks.

---

### Post by steeldriver on 2012-05-20
I'm not a fortran guy but maybe you need an equivalent -J/path/to/.mod (or equivalent appended to your MOD_PATH) to pick up the actual compiled modules?

---

### Post by MadCow108 on 2012-05-21
are you using mpif90/mpif77 to compiler your program? if not you should
less recommended alternative:
use
```
mpif90 --showme:compile
mpif90 --showme:link

#outputs for openmpi:
-I/usr/lib/openmpi/include -pthread -I/usr/lib/openmpi/lib

-pthread -I/usr/lib/openmpi/lib -L/usr/lib/openmpi/lib -lmpi_f90 -lmpi_f77 -lmpi -lopen-rte -lopen-pal -ldl -Wl,--export-dynamic -lnsl -lutil -lm -ldl


```
to get the needed flags

---

