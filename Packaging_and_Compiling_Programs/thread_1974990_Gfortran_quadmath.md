---
title: "Gfortran quadmath"
date: 2012-05-06
forum: Packaging and Compiling Programs
---

### Post by jesse.johns on 2012-05-06
Hello,

I am trying to compile a program, and during the configuration stage, I am greeted with:

configure:1435: checking whether the Fortran 90 compiler (mpif90  ) works
configure:1446: mpif90 -o conftest   conftest.F  1>&5
/usr/bin/ld: warning: libquadmath.so.0, needed by /usr/lib/gcc/x86_64-linux-gnu/4.4.5/libgfortran.so, not found (try using -rpath or -rpath-link)
/usr/lib/gcc/x86_64-linux-gnu/4.4.5/libgfortran.so: undefined reference to `ccosq@QUADMATH_1.0'
/usr/lib/gcc/x86_64-linux-gnu/4.4.5/libgfortran.so: undefined reference to `cexpq@QUADMATH_1.0'
/usr/lib/gcc/x86_64-linux-gnu/4.4.5/libgfortran.so: undefined reference to `asinq@QUADMATH_1.0'
(... the list goes on, so I truncated it)

So, I am missing libquadmath.so.0... I couldn't find it either.  I am not certain where to find this package, since it seems to be unavilable for this gcc version?  I have compiled it previously on this same system, but I updated my gcc since then... reverting back does not help, either.

Any help would help would be greatly appreciated it.

Thanks.

---

