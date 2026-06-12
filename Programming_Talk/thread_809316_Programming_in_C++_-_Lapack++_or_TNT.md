---
title: "Programming in C++ - Lapack++ or TNT"
date: 2008-05-27
forum: Programming Talk
---

### Post by bernoulli on 2008-05-27
Hi. I'm interested in making some programs in mathematics/signal analysis in C++, and I cannot figure out what packages to use, lapack++ or tnt? Any one else? What about packages for Fourier analysis?

---

### Post by Joeb454 on 2008-05-27
What do you want to use the packages for? For writing the code? If so the standard text editor in Ubuntu supports C/C++ syntax highlighting :)

---

### Post by sdennie on 2008-05-27
I've not looked at the BLAS/LAPACK interfaces for C++ (or TNT at all) but, if you are even vaguely concerned with performance, I'd be very wary of any OO interface to those libraries.  As for FFTs, I believe they are included in LAPACK (at least they are/were in Suns implementation).

Edit:
Oh, FFT stuff is included in FFTPACK I think.  That just happens to come with many vendors BLAS/LAPACK packages.

---

### Post by Golem XIV on 2008-05-27
You may want to take a look at [numerical recipes]("http://www.nr.com/")

---

### Post by bernoulli on 2008-05-27
Yes, I want to write actual C++ code to perform certain tasks in mathematics and signal analysis. 

I've done tutorials on C++ and I think I have the basic stuff in order. The problem comes when I want to do some scientific programming. I'm not sure which packages (or is it libraries?) to use, and how to install some of them.

---

### Post by sdennie on 2008-05-27
If you are fairly new to C++ and Ubuntu, I would recommend going to System->Administration->Synaptic Package Manager and searching for lapack.  Look for the packages with the Ubuntu icon by them (excluding the two python packages) and install them.  I think that will give you the standard FORTRAN versions of BLAS/LAPACK with C interfaces to them.  Those interfaces should be callable from C++ but, without the likelihood of shooting yourself in the foot with a higher level interface to perfectly good function calls/data structures.

---

### Post by bernoulli on 2008-05-27
I've decided to go for IT++, which is supposed to be an alternative to Lapack++. On first glance it looks a bit similar to Matlab-notation.

I downloaded and installed IT++ through the "Synaptic Package Manager", but I can not seem to compile simple test programs. If I try this straight forward line:
```
g++ -o test-itpp test-itpp.cpp
```
I will get errors like
```
test-itpp.cpp:(.text+0x10f): undefined reference to `itpp::Vec<double>::Vec(int, 
itpp::Factory const&)'
```

When I try to follow the first section on their webpage ([http://itpp.sourceforge.net/current/linking.html](http://itpp.sourceforge.net/current/linking.html)), i.e. with the command:
```
g++ `pkg-config --cflags itpp` -o test-itpp test-itpp.cpp `pkg-config --libs itpp`
```

I get this:
```
/usr/bin/ld: cannot find -lcblas
collect2: ld returned 1 exit status
```

Now, I got this earlier too, with -llapack and -lfftw3. I solved this by installing these again. I just looked in the folder /usr/lib/ and saw now that I have the files liblapack.la and libfftw3.la (and .a), but I do not have this with cblas. I only have libcblas.so.3 and libcblas.so.3.0  (all are shared libraries). Does anyone have any ideas on what I can do? I can't find cblas in "Synaptic Package Manager", but these should have been installed at the same time with IT++, right? I remember there was many other packages that were installed at the same time, including fftw3.

I guess I'm to used to things working right out of the box.

---

### Post by bernoulli on 2008-05-27
Hmm. It looks like it works now after I installed "atlas3-base-dev" and "atlas3-headers". I already had "atlas3-base". 

I will have to test it some more later...

---

### Post by jeremytaylor on 2008-05-28
If you're looking for an easy to use OO matrix library then you might like to try newmat
[http://www.robertnz.net/nm_intro.htm](http://www.robertnz.net/nm_intro.htm)

You'll drop a few performance points but not as many as you might think.

Jeremy

---

### Post by bernoulli on 2008-05-28
Thanks, but for now I'm pretty happy with IT++.

---

