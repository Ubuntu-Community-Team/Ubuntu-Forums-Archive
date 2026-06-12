---
title: "libgfortran.so.3: version GFROTRAN_1.4 not found"
date: 2013-01-23
forum: Packaging and Compiling Programs
---

### Post by lulucas on 2013-01-23
I installed an ubuntu with gcc 4.4.0, and I want to use matlab which only supports gcc 4.3.4, so I installed gcc 4.3.4. Then I install the lapack package, it comes to the error:

make[1]: Entering directory `/home/lucas/.local/share/Trash/files/lapack-3.2.4.2/INSTALL'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lucas/.local/share/Trash/files/lapack-3.2.4.2/INSTALL'
./testlsame: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testlsame)
./testslamch: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testslamch)
./testdlamch: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testdlamch)
./testsecond: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testsecond)
./testdsecnd: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testdsecnd)
./testieee: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testieee)
./testversion: /usr/local/gcc-4.3.4/lib/libgfortran.so.3: version `GFORTRAN_1.4' not found (required by ./testversion)
make: *** [lapack_install] Error 1

how to solve it?

---

