---
title: "fortran Matrix multiply fast ? DGEMM BLAS vs. MATLAB"
date: 2009-10-19
forum: Programming Talk
---

### Post by cholericfun on 2009-10-19
Hi all,
this is not one of those "urgent help" threads, just a bit of learning by doing.


i'm testing out speeds with various implementations of Matrix-Matrix multiplications in fortran with 2 random (1000,1000) matrixes


basically it is: 

       ```
    do j=1,1000
         do k=1,1000
          do i=1,1000
        c(i,j)=c(i,j)+a(i,k)*b(k,j)
          enddo
         enddo
        enddo
```

in the fortran optimal jki-form.

i've just looked into the BLAS routine DGEMM and found the basic algorithm being essentially the same as above 
```
        do j=1,1000
         do k=1,1000
          TEMP=b(k,j)
          do i=1,1000
            c(i,j)=c(i,j)+TEMP*a(i,k)
          enddo
         enddo
        enddo
```

with about the same time consumption in my test problem
what irritates me is that in MATLAB, i only need 1/4 of the time for the exact same problem by typing A*B (not when typing in the loops of course...)

i wonder how Matlab does that (octave takes about 5/4 the fortran time), also is my "interpretation" of BLAS - DGEMM.f correct or have i missed something? i havent tried linking it because i want to see what the optimal code is and not just look at times (ok, plus i wouldnt even know how to but i can read up on that)...


thanks a lot for everyones patience :)


edit: actually i just compiled with -O3 flag, suddenly the textbook version is down to almost the matlab-speed, but the DGEMM version stays almost the same...
ok, i will have to read that code more carefully. 
still though, i get 0.80 seconds in matlab and 1.01 seconds in fortran so thats +1/4 slower.

---

### Post by MadCow108 on 2009-10-19
matlab probably uses hand optimized code for matrix multiplication whereas your fortran code relies on compiler optimizations which are very good in fortran but probably not as good as matlabs human written.
Optimizations include aligning the data and instructions to fit into the LX caches of the cpu and such kind of low level stuff.

but 25% difference is also not very significant especially on a desktop machine.

---

### Post by cholericfun on 2009-10-19
well, 25% is not that small, of course this is a toy application and the timing differences by changing around the do loop order is (ijk,jik,kji...) are more significant.

i'm just curious - thats why i'm posting. plus i thought BLAS would be fastest (though i didnt read through their code again yet).

hm, is there a way to check cache size in fortran in order to write portable code? (ok guess not?)

---

### Post by MadCow108 on 2009-10-19
if you change the loop order you change the memory layout.
this has a big impact on the performance it influences how effective the computer can pull whole matrix rows/columns into cache.

The BLAS algorithm could be the fastest, but the compiler does not know what its optimizing and for which purpose (compilers don't think) and probably fails to optimize it properly.

you may be interested in the atlas library:
[http://math-atlas.sourceforge.net/](http://math-atlas.sourceforge.net/)
it has very high performance linear algebra algorithms and there are also quite a few papers on the subject on the page.

---

### Post by TheStatsMan on 2009-10-19
Using an optimised version of BLAS will make a large difference. I just compared the non-optimised routine to the ATLAS version. This was for the problem you described. The timing also included the construction of the 1000x1000 matricies and filling two of them with random numbers

ATLAS
```

real    0m0.460s
user    0m0.432s
sys    0m0.028s

```

Standard version
```

real    0m2.112s
user    0m2.072s
sys    0m0.020s

```

The standard version was compiled using gfortran with the following flags
```

-march=core2 -ffast-math -funroll-loops -O3

```

This is just the standard version of ATLAS as well not the threaded version. I haven't played around with the threaded version as we use the MKL library at work, which is substantially faster and threaded. From what I understand the latter versions of MATLAB use a threaded version of BLAS.

Just for comparison I have also done a numpy version using python

```

real    0m0.734s
user    0m0.708s
sys    0m0.024s

```

Numpy uses ATLAS and you can see even with the additional overhead it is still substatially quicker than the non-optimised version. Once again the timing include the construction of the matricies and filling them with random numbers

```

from numpy import*

A=random.randn(1000,1000)
B=random.randn(1000,1000)
C=dot(A,B)

```

---

### Post by rusi_pathan on 2009-10-30
> **cholericfun said:**
> Hi all,
this is not one of those "urgent help" threads, just a bit of learning by doing.


i'm testing out speeds with various implementations of Matrix-Matrix multiplications in fortran with 2 random (1000,1000) matrixes


basically it is: 

       ```
    do j=1,1000
         do k=1,1000
          do i=1,1000
        c(i,j)=c(i,j)+a(i,k)*b(k,j)
          enddo
         enddo
        enddo
```

in the fortran optimal jki-form.

i've just looked into the BLAS routine DGEMM and found the basic algorithm being essentially the same as above 
```
        do j=1,1000
         do k=1,1000
          TEMP=b(k,j)
          do i=1,1000
            c(i,j)=c(i,j)+TEMP*a(i,k)
          enddo
         enddo
        enddo
```

with about the same time consumption in my test problem
what irritates me is that in MATLAB, i only need 1/4 of the time for the exact same problem by typing A*B (not when typing in the loops of course...)

i wonder how Matlab does that (octave takes about 5/4 the fortran time), also is my "interpretation" of BLAS - DGEMM.f correct or have i missed something? i havent tried linking it because i want to see what the optimal code is and not just look at times (ok, plus i wouldnt even know how to but i can read up on that)...


thanks a lot for everyones patience :)


edit: actually i just compiled with -O3 flag, suddenly the textbook version is down to almost the matlab-speed, but the DGEMM version stays almost the same...
ok, i will have to read that code more carefully. 
still though, i get 0.80 seconds in matlab and 1.01 seconds in fortran so thats +1/4 slower.

You should never write you own dense matmul routine (unless your name is Kazushige Goto) because you wont be able to achieve good performance.

The reason MATLAB is fast is because it uses a vendor supplied BLAS (eg MKL) underneath. See the following link:

[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/rn/f14-998197.html#f14-1009978](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/rn/f14-998197.html#f14-1009978)

MATLAB is bascially an expensive dumbed down wrapper around LAPACK (written in Fortran and built on top of BLAS), BLAS (written either in C, Fortran or assembly) and some other libraries such as FFTW, Chlomod etc. with built in viz and a tonne of bloat. Its funny that they can make people pay for it.

---

### Post by cholericfun on 2009-10-30
> **rusi_pathan said:**
> (unless your name is Kazushige Goto) 

haha, not quiet, was just playing around though, as an exercise.
havent come around to play around with it much more though, and  its harly gonna be to anybodys benefit if i did..

---

