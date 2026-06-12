---
title: "g77 compiles f77 fails"
date: 2011-12-02
forum: Programming Talk
---

### Post by mrplow on 2011-12-02
Hi all, I'm trying to compile nec2dXs_VM from the website and links below. The Numerical Electromagnetics Code (NEC) is a popular antenna modeling software package for wire and surface antennas - wikipedia.
I'm using NEC to optimizing some UHF antennas for digital OTA tv broadcast. Its a slow process involving running thousands of slight variations of an antenna model and using NEC to analyze the model, eventually leading to a highly optimized antenna tuned to a specific frequency.
I've used the nec package from the ubuntu repositories and it does work. The only problem is its slow, and tends to lock up from time to time (no idea why, it works perfect all the time on one of my computers and freezes every few hours on two of my other computers, all running oneiric.) So I'd like to try using a few different variations to see if there are any differences.

First off I am not a programmer, I don't know fortran or c but I'm good at cut and paste! I can compile from source if there is a good readme.
Compiling using g77 in ubuntu hardy works as it should, but I'm not sure how to get the resulting binaries working in oneiric. Its probably to do with missing depreciated libraries. I'm not sure how to 'embed' libraries, or if that would work.
I'm looking for speed, the size of the resulting binary doesn't matter.
However using f77 in oneiric I'm getting syntax errors. I tried using intel's ifort compiler but it gives me a syntax error for the same line as well but it gives more details.
Could someone please give me a few hints.

```
/opt/intel/bin/ifort -f77rtl nec2dxs.f
nec2dxs.f(7120): error #5082: Syntax error, found '+' when expecting one of: ( * , % [ /
      DATA NDIMN,NDIMNP/netmx,netmx+1/,TP/6.283185308D+0/       ! av06
-----------------------------------^
nec2dxs.f(7120): error #6946: In this DATA statement, there are more values assigned to variables then there are variables.  There must be the same number of values and variables.   [1]
      DATA NDIMN,NDIMNP/netmx,netmx+1/,TP/6.283185308D+0/       ! av06
^
compilation aborted for nec2dxs.f (code 1)
```

[http://www.si-list.net/swindex.html](http://www.si-list.net/swindex.html)
[http://www.si-list.net/NEC_Archives/Nec2dXS_VM.zip](http://www.si-list.net/NEC_Archives/Nec2dXS_VM.zip)

---

### Post by 3Miro on 2011-12-02
This software hasn't been updated since 2005, which isn't very good. Compilers change over time and eventually you end up with code that just doesn't compile.

The best you can do is to install an older version of gcc. You can go to the Software Center and look for gcc. The 11.10 default version is 4.6, get an older one, maybe 4.3 or 4.2 if they are available. You should also install older versions of gfortran.

For the new command you should change the compile command to something like:
```
g77-4.3 ....
```

---

### Post by Bachstelze on 2011-12-02
> **3Miro said:**
> This software hasn't been updated since 2005, which isn't very good. Compilers change over time and eventually you end up with code that just doesn't compile.

This was a joke, right?

---

### Post by 3Miro on 2011-12-02
> **Bachstelze said:**
> This was a joke, right?

What do you mean? The page claims that it was last updated in 2005. Then old code not compiling on the new compiler is quite common. It does depend on the code and perhaps on the way the code has been written, but often times old code will fail on new compilers.

---

### Post by Bachstelze on 2011-12-02
> **3Miro said:**
> What do you mean? The page claims that it was last updated in 2005. Then old code not compiling on the new compiler is quite common. It does depend on the code and perhaps on the way the code has been written, but often times old code will fail on new compilers.

No. Old code fails on new operating systems or new libraries. Not on new compilers.

---

### Post by 3Miro on 2011-12-02
> **Bachstelze said:**
> No. Old code fails on new operating systems or new libraries. Not on new compilers.

Each compiler does come with its own set of at least some of the libraries. For all intensive purposes it is the compiler.

---

### Post by Bachstelze on 2011-12-02
> **3Miro said:**
> Each compiler does come with its own set of at least some of the libraries.

Proof ?

---

### Post by 3Miro on 2011-12-02
> **Bachstelze said:**
> Proof ?

I will have to ask my sister for the example, she was given code from one of her teachers and it was some old fortran code. Depending on the compiler, it either compiles and runs fine, compilers and produces garbage results or doesn't compile at all. I don't know exactly why it happens, I don't know enough about compilers, but it does happen.

---

### Post by Petrolea on 2011-12-02
> **Bachstelze said:**
> Proof ?

It's a pretty common thing, I remember this happening on Windows all the time (that's why it's always a good idea to follow standards and not use the code that's compiler specific).

Also, try searching for "compiler specific libraries".

---

### Post by Bachstelze on 2011-12-02
Well here we have two different compilers that behave differently, obviously one of them is wrong: either the code is valid or it is not valid...  And it has nothing to do with libraries at all so I guess this discussion is off-topic. :p

@mrplow: Ask someone knowledgeable in Fortran. f77 complains of a syntax error, it may be something very minor.

---

### Post by 3Miro on 2011-12-02
One learns something new every day.

Here is an example, on Ubuntu 11.10 with gfortran 4.5 the code compiles and runs. With gfortran 4.6 it fails to compile. In this case I think it is a syntax problem, someone isn't following specifications, but for one reason or another, compiler versions do matter.

---

### Post by mrplow on 2011-12-02
thanks, I didn't expect so many quick replies. I installed g77 and all its dependencies from hardy and got it to compile. g77 seems more lenient for slightly broken code. In the end this version of nec turned out to be quite a bit slower.

---

### Post by 3Miro on 2011-12-02
> **mrplow said:**
> thanks, I didn't expect so many quick replies. I installed g77 and all its dependencies from hardy and got it to compile. g77 seems more lenient for slightly broken code. In the end this version of nec turned out to be quite a bit slower.

If you have solved your issue, could you please mark the thread as [Solved].

---

