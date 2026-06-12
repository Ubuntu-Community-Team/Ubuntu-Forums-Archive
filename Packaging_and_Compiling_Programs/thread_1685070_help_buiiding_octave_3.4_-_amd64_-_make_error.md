---
title: "help buiiding octave 3.4 - amd64 - make error"
date: 2011-02-10
forum: Packaging and Compiling Programs
---

### Post by waspbr on 2011-02-10
Hey guys, I am a little stuck with this so I thought I would ask the ubuntu hivemind for help. 

Anyway I have been trying to biuld he newest stable octave into this amd64 box and though I was able to ./configure I keep getting this make error. 
```
make  all-recursive
make[1]: Entering directory `/home/user/Sources/octave-3.4.0'
Making all in libgnu
make[2]: Entering directory `/home/user/Sources/octave-3.4.0/libgnu'
make  all-recursive
make[3]: Entering directory `/home/user/Sources/octave-3.4.0/libgnu'
make[4]: Entering directory `/home/user/Sources/octave-3.4.0/libgnu'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/user/Sources/octave-3.4.0/libgnu'
make[3]: Leaving directory `/home/user/Sources/octave-3.4.0/libgnu'
make[2]: Leaving directory `/home/user/Sources/octave-3.4.0/libgnu'
Making all in libcruft
make[2]: Entering directory `/home/user/Sources/octave-3.4.0/libcruft'
/bin/sh ../libtool  --tag=F77   --mode=compile f77  -O -c -o arpack/src/libcruft_la-cgetv0.lo `test -f 'arpack/src/cgetv0.f' || echo './'`arpack/src/cgetv0.f
libtool: compile:  f77 -O -c arpack/src/cgetv0.f  -fPIC -o arpack/src/.libs/libcruft_la-cgetv0.o
Cannot open file debug.h
/usr/bin/f77: aborting compilation
make[2]: *** [arpack/src/libcruft_la-cgetv0.lo] Error 1
make[2]: Leaving directory `/home/user/Sources/octave-3.4.0/libcruft'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/Sources/octave-3.4.0'
make: *** [all] Error 2
```

I would appreciate any input, I am a bit of a noob at this so please bear with me.

As for the dependencies, I used:
```
sudo apt-get build-dep octave3.2
```

cheers

---

### Post by rmcd on 2011-02-10
I don't know the answer to your question, but I wanted to let you know that I did successfully build 3.4.0 with amd64 on 10.04, so it is possible. I'm pretty sure I also ran build-dep octave3.2, but I would have done it a while back.

Which version of ubuntu are you using?

---

### Post by waspbr on 2011-02-10
maverick, do you remember if you simply used ./configure or you used any other parameters? hmm, didn't think there was such a big difference between karmic and maverick

---

### Post by rmcd on 2011-02-10
I was installing for all users, so I ran 

./configure --prefix=/opt/octave

as root.

Also, I just ran "make" then "make check" (to be sure all was well), then "make install". I'm not a noobie at Linux but I am at building software. Did you try it without "all-recursive"?

---

### Post by waspbr on 2011-02-11
Stil no luck, though I am not sure what you meant by running without the all-recursive. [oh, I get it now, though that was part of output, the command I typed was a simple "make"]

Anyway, I tried to build on my laptop that is also running maverick and I got the same error, so something rather crucial must have changed between karmic and maverick. I will try to look into it when I get home from work.

---

### Post by gmargo on 2011-02-11
I just finished building it on 64-bit 10.10 Maverick.  It compiled and passed its own tests.  

One difference: I used **gfortran** (which is a Fortran 95 compiler) not the **f77** you seem to be using.  Where did **f77** come from?  I don't see that in the repositories.

In the "aptitude build-dep" stage, I kept libgl1-mesa-dev instead of replacing it with libgl1-mesa-swx11-dev, but that shouldn't matter.

---

### Post by waspbr on 2011-02-11
That seems to have done it, no errors so far. I am not sure where the f77 comes from, I guess it must have been a dependency for another package, but anyway I have removed all the packages related to f77 and installed gfortran 4.5. 

so far so good, unless I have any more problems I will mark this thread as solved. 

Thanks though.

UPDATE: I am happy to report that everything went well with gfortran, I had hit another error, but that was just because I forgot to do a  "make clean" before attempting to make again.

again, thanks a lot for the help.

---

### Post by daryl314 on 2011-02-19
i'm having trouble compiling for i386, and am getting the same f77 error.  what did you do to remove the packages related to f77?

i installed the gfortran-4.5 package, and that didn't seem to solve the problem.

---

### Post by MadCow108 on 2011-02-19
did you rerun the configure script?
maybe run a *make distclean* first to start from scratch

---

### Post by gmargo on 2011-02-19
> **daryl314 said:**
> what did you do to remove the packages related to f77?


You should be able to find the package providing f77 with dpkg:
```

$ dpkg -S $(which f77)

```

---

### Post by daryl314 on 2011-02-20
installing dependencies using 'sudo apt-get build-dep octave3.2' and removing the fort77 package did the trick for me.

thanks!

---

