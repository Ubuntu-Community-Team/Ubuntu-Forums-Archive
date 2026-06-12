---
title: "gdb ./sysdeps/ieee754/dbl-64/s_sin.c: No such file or directory."
date: 2015-09-15
forum: Programming Talk
---

### Post by xadder on 2015-09-15
Hi!

I'm trying to debug a fortran'95 program with gdb, but as soon as I try to step past a cosine function I get:

(gdb) 
__cos (x=3.2879134073186327) at ../sysdeps/ieee754/dbl-64/s_sin.c:513
513	../sysdeps/ieee754/dbl-64/s_sin.c: No such file or directory.
(gdb)

Searching for help, I wonder if this is some mis-match between 32bit and 64bit, but I' not sure. I am using a 32-bit system with uname -a returning: 

Linux X220 3.19.0-28-generic #30-Ubuntu SMP Mon Aug 31 15:52:10 UTC 2015 i686 i686 i686 GNU/Linux

Thanks!

---

### Post by dwhitney67 on 2015-09-15
Do you have that file on your system?  The error "No such file or directory" is not meant to be an ambiguous statement.

---

### Post by xadder on 2015-09-15
No, in fact I don't seem to have that other bits of thatdirectory tree either:

$locate s_cos.c

$locate ieee754
/usr/include/i386-linux-gnu/ieee754.h

$locate sysdep
/usr/share/octave/3.8.2/etc/tests/libinterp/corefcn/sysdep.cc-tst

---

### Post by dwhitney67 on 2015-09-15
It seems to me that you are using a library (undoubtedly written in C), but for which you do not have the source code; all you have are the shared and/or static library file(s).

Without such source files, and furthermore without symbolic information in the library file(s), you will not be able to step into these functions of interest.  I suggest using 'next' in lieu of 'step' when debugging.

---

### Post by steeldriver on 2015-09-15
/sysdeps/ieee754/dbl-64/s_sin.c is down in the bowels of eglibc I think - you can browse the source at 

[http://www.eglibc.org/cgi-bin/viewvc.cgi/branches/eglibc-2_19/libc/sysdeps/ieee754/dbl-64/](http://www.eglibc.org/cgi-bin/viewvc.cgi/branches/eglibc-2_19/libc/sysdeps/ieee754/dbl-64/)

for example - or download the Ubuntu source package using apt-get

---

### Post by xadder on 2015-09-15
Hi Guys,

Thanks for the tips, but I'm still stuck. I am using gdb from the repos (GNU gdb (Ubuntu 7.9-1ubuntu1) 7.9), and likewise gfortran (GNU Fortran (Ubuntu 4.9.2-10ubuntu13) 4.9.2).

I tried using next instead of step, but now get problems with 'libc-start.c: No such file or directory'. I installed linux-libc-dev to try to get around this, but it hasn't helped.

I also can't find elibc in the repos, just libc (which didn't help)

By the way, my original Makefile had some complex options

F90=gfortran -g  -pedantic -Wall -fbounds-check -fdefault-real-8 -finit-real=nan -ffree-line-length-none 

Reducing this down to just gfortran -g I now get:
../sysdeps/i386/i686/multiarch/strcat.S: No such file or directory.

I have gbd-multiarch installed, but not in any sysdeps directory, and in this case no sign of strcat.S.

---

### Post by xadder on 2015-09-15
OK, some progress.

If I keep the simple options for gfortran -g

and use gdb-multiarch on the executable

and then I can use step until I get to the cos 

then next to get past that and other trig/math statements.

Not ideal, but I can work with this for now and hope that things improve with the next Ubuntu upgrade. I also tried ddd --debugger gdb-multiarch  and that worked fine (again, being careful to use next and not step as needed).

Thanks for the tips!

---

### Post by dwhitney67 on 2015-09-15
Use 'next' to execute the next statement in your code; only use 'step' to enter a function.  Once inside the function (if possible), then you should resume using 'next'.

Btw, you should look into use the Data Display Debugger (ddd), which is a GUI front-end to gdb.

---

