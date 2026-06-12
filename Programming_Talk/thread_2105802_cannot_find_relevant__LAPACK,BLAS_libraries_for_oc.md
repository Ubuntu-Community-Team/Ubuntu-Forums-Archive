---
title: "cannot find relevant  LAPACK,BLAS libraries for octave 3.6.3"
date: 2013-01-17
forum: Programming Talk
---

### Post by fr33c0untry on 2013-01-17
hi,
i installed octave 3.2.4 form the software center a few months ago but realised it was a very old version.so i decided to download the latest one (3.6.3) from the website.i have never compiled from the source before but learnt about it from a tutorial.
 
i get an error after typing ./configure showing that LAPACK AND BLAS libraries are not found.i downloaded synaptic manager and downloaded the relevant libraries from the universe and multiverse category.but i'm still stuck with this error.

how do i find out the exact name of the libraries needed?
would trying with a less recent release avoid this error?
 thanks in advance

---

### Post by steeldriver on 2013-01-17
did you get the -dev packages? (libblas-dev and/or liblapack-dev) iirc you will need those (not just the runtime libblas3gf or whatever) to actually build stuff

---

### Post by fr33c0untry on 2013-01-18
hi steeldriver
i have installed both of them (liblapack and libblac) it says they're static libraries (not sure what that means)but still no progress in compiling.

here's what i get towards the end before the error shows up:
```

checking if sgemm_ is being linked in already... no
checking for ATL_xerbla in -latlas... no
checking for sgemm_ in -lblas... yes
checking for dgemm_ in -ldgemm... no
checking for sgemm_ in -lmkl... no
checking for sgemm_ in -framework vecLib... no
checking for sgemm_ in -lcxml... no
checking for sgemm_ in -ldxml... no
checking for sgemm_ in -lscs... no
checking for sgemm_ in -lcomplib.sgimath... no
checking for sgemm_ in -lblas... (cached) yes
checking for sgemm_ in -lessl... no
checking for sgemm_ in -lblas... (cached) yes
checking whether LSAME is called correctly from Fortran... yes
checking whether ISAMAX is called correctly from Fortran... yes
checking whether SDOT is called correctly from Fortran... yes
checking whether DDOT is called correctly from Fortran... yes
checking whether CDOTU is called correctly from Fortran... yes
checking whether ZDOTU is called correctly from Fortran... yes
checking whether the integer size is correct... yes
checking for cheev_... no
checking for cheev_ in -llapack... no
checking for cheev_ in -llapack_rs6k... no
configure: error: You are required to have BLAS and LAPACK libraries

```

---

### Post by steeldriver on 2013-01-18
Hmm well from that output it seems to be finding libblas so I don't think the actual libraries are necessarily the problem

What release / version of Ubuntu are you running? for the record, here is what works for me:

```
$ sudo apt-get install build-essential autoconf automake \
gfortran libpcre3-dev libatlas-dev liblapack-dev libreadline6-dev \
texinfo texlive-base
```IIRC it will configure and build without the tex packages, but you lose the inline help. This is on a 12.04 Server box so configure warns about being unable to find graphics:

```

configure: WARNING: I didn't find the necessary libraries to compile native
configure: WARNING: graphics.  It isn't necessary to have native graphics,
configure: WARNING: but you will need to have gnuplot installed or you won't
configure: WARNING: be able to use any of Octave's plotting commands
configure: WARNING:
configure: WARNING: I didn't find gnuplot.  It isn't necessary to have gnuplot
configure: WARNING: installed, but you won't be able to use any of Octave's
configure: WARNING: plotting commands without it.

```and the 'make' fails right at the end when it tries to create a dvi, but the build essentially completes and basic command-line testing with ./run-octave works

---

### Post by MadCow108 on 2013-01-18
have a look in the config.log for more detailed error messages.

you could also try to compile the octabe 3.6.3 package from ubuntu raring
the configure runs through fine for me in precise with that package (I did not fully build it though)
```
pull-lp-source octave
cd octave-*
mk-build-deps -ir #requires devscripts and equivs
debuild -us -uc
```
you can also use the *backportpackage* script if you have a ppa or working pbuilder chroot

---

### Post by fr33c0untry on 2013-01-19
i found out yestarday that the software center does have octave 3.6.3.it downloaded fine but i noticed that it was not able to plot 3d graphs and execute the eig() command instead it would close by itself.
my ubuntu release is Release 12.04 (precise) desktop

---

### Post by fr33c0untry on 2013-01-19
for example when i type sphere to plot a sphere i get:
```

octave: symbol lookup error: /usr/lib/liblapack.so.3gf: undefined symbol: ATL_idamax


```

---

### Post by fr33c0untry on 2013-01-19
for example when i type sphere to plot a sphere i get:
```

octave: symbol lookup error: /usr/lib/liblapack.so.3gf: undefined symbol: ATL_idamax


```

---

### Post by fr33c0untry on 2013-01-19
i think everything is working fine now.got an advice from someone.it seems that the ATLAS library was the culprit all along because of some configuration problem.according to him he suggested to completely remove the atlas library by typing the command
'sudo apt-get purge libatlas3gf-base'
3d plotting and matrix manipulations worked fine after that.
hope there aren't anymore problems ahead
thanks MadCow108 and steeldriver for your help.would have given up on octave otherwise

---

