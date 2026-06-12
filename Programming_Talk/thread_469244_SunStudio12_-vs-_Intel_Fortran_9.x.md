---
title: "SunStudio12 -vs- Intel Fortran 9.x"
date: 2007-06-09
forum: Programming Talk
---

### Post by jdrodrig on 2007-06-09
I have been experimenting with Sun's newly released SunStudio12 for Linux, and in particular with its Fortran Compiler (8.3) on both a Pentium M (Banias) and on a 4xOpteron275 machines.

I was of course expecting Intel's to produce faster core on a Pentium M, but I am still surprised Intel's is significantly faster on the Opteron computer  (after all Sun have been using Opteron on their machines for the last few years)... are you guys finding any speed advantage of the Sun's compilers?

My code is rather simple. Some numerical optimization using bilinear interpolation. I use OpenMP to split the grid proportional to each core.

On the Banias I use, ifort xyz.f90 -O3 -xB -axB -ip
                                  f95 xyz.f90  -fast

On Opteron I use,    ifort xyz.f90 -O3 -xW -axW -ip -openmp
                                 f95 xyz.f90 -fast -openmp -m32

The -m32 is to force the compiler to generate 32 bit code, to make it comparable with what ifort generates. The -m64 generates even slower code on my simple program.

It is nice to have an IDE for Fortran on Linux but I was hoping for speed advantages also.

UPDATE. After some more testing, it seems I spoke too fast. Now I am getting identical performance, once I include the -xipo=2 (interprocedural optimizations) and -xvector=simd (vectorization).

---

