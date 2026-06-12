---
title: "Problem linking to Intel MKL"
date: 2006-10-02
forum: Programming Talk
---

### Post by renormalize on 2006-10-02
I'm not yet a particularly savy linux user, but I have managed to install Intel Fortran, C++, and MKL on my PC's Ubuntu 6.06 partition.  Now I want to use the free Fortran package PROPACK to do singular value decompositions of large sparse matrices.  Using the make file included with PROPACK works fine until it tries to link and optimize the example programs included with the package:

make[2]: Entering directory `/home/ron/Desktop/PROPACK/double/Examples'
ifort -cm -w95 -assume buffered_io -vec_report0 -O3 -ipo -xN -Vaxlib   -o example.LINUX_ICC_IA32.x example.o matvec.o -L/opt/intel/mkl/8.1.1/lib/32 -L.. -L. ../libdpropack_LINUX_ICC_IA32.a ../libdlapack_util_LINUX_ICC_IA32.a -lmkl_p4 -lguide ../libdlapack_util_LINUX_ICC_IA32.a
IPO: performing multi-file optimizations
IPO: generating object file /tmp/ipo_ifort4usUFH.o
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `vsCos'
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `vslDeleteStream'
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `vdSin'
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `viRngUniformBits'
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `vslNewStream'
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `vdCos'
/opt/intel/mkl/8.1.1/lib/32/libmkl_p4.so: undefined reference to `vsSin'
make[2]: *** [example.LINUX_ICC_IA32.x] Error 1
make[2]: Leaving directory `/home/ron/Desktop/PROPACK/double/Examples'

I figured out that the above undefined references are functions from the Intel VML/VSL package, so I added -lmkl_vml_p4 after -lmkl_p4 in the above ifort line, but it still generates the same errors.

Any insights or suggestions?

Thanks,
Ron

---

### Post by mezhaka on 2009-04-14
was there any resolution? i got a similar problem.

---

### Post by Arndt on 2009-04-14
> **mezhaka said:**
> was there any resolution? i got a similar problem.

What I would do in that situation would be to use the 'nm' program to see where the undefined symbols are used, and if they are defined in any archive file I have. And the rest ought to be to put the archive files in the right order on the link line.

There are flags one can give to the linker, to make it show what it's doing, but if it doesn't find a thing, it can't say where it is, so I haven't found those flags very useful.

---

### Post by mezhaka on 2009-04-15
> **mezhaka said:**
> was there any resolution? i got a similar problem.

here's my story. the order of parameter for icc matters.
this does not work
```
icc -w -DMKL_VML_MIXED -I/path/to/include -L/path/to/lib/64 -lmkl_ipf intel.sandbox.cpp
```
but this does:
```
icc -w -DMKL_VML_MIXED -I/path/to/include intel.sandbox.cpp -L/path/to/lib/64 -lmkl_ipf
```
**period**


here's intel.sandbox.cpp:
```

#include "mkl_vsl.h"

int main() {
    VSLStreamStatePtr stream_state;                  
    vslNewStream( &stream_state, VSL_BRNG_R250, 1232);
}

```

btw, i figured that out reading the examples wich where in MKL distribution, particularly /path/to/mkl81/examples/vslc/makefile

---

