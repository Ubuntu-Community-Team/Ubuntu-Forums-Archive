---
title: "fortran compile problem"
date: 2005-12-17
forum: Programming Talk
---

### Post by DaveRowell on 2005-12-17
I'm new to Linux and Linux programming.  I've had Synaptic install g77-3.4 and g77-3.4-doc which installed gcc-3.4 on Ubuntu 5.1.

To relearn Fortran I want to work through Page's "Professional Programmer's Guide to Fortran 77".  Here's his very first program:

      PROGRAM TINY

      WRITE(UNIT=*, FMT=*) 'Hello, World' 

      END 


When I try to compile tiny.f I get this error generated, I'd guess, by the linker:


david@CPQ1265:~$ g77-3.4 /home/david/Programming/Source/tiny.f 
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
david@CPQ1265:~$

I'm confused!  Would one of you be kind enough to tell me what I've done wrong?

---

### Post by toojays on 2005-12-17
Have you installed the "build-essential" package?

---

### Post by DaveRowell on 2005-12-17
And the build essential would be?

---

### Post by toojays on 2005-12-17
There is a package called "build-essential", which includes some development files necessary to build programs. A common problem that comes up in this forum is people trying to compile programs when they have installed gcc (or in your case, g77) without installing build-essential as well.

---

### Post by Van_Gogh on 2005-12-17
This may be slightly off-topic, but is there a special reason you want to use Fortran 77 instead of the newer Fortran 90/95? There even are open-source compilers available(GFortran and g95).

cheers

---

### Post by DaveRowell on 2005-12-18
By golly, that worked just fine - thanks a million!  The output executable will always default to the home folder?  Run it with ./a.out?

Using G77 only because I have some documentation for Fortran 77 and know that G77 has the capability to do what I need.  I ran G77 under Windoze 4 or 5 years ago and grew to trust it but I've forgotten much of what I was beginning to learn.  With the extensions built into G77 I think it has the features I need from Fortran 90 anyway.  I probably should try Fortran 90 and may well do that in the not too distant future but right now I'm still in the "lets learn about and evaluate Linux" mode.  G77 is a LOT better than the FORTRAN I "learned" in the summer of '65!!!

---

### Post by toojays on 2005-12-18
I haven't used g77, but with the other GNU programs, you can select the name of the output file with the -o option. e.g. "g77 -o tiny tiny.f

---

### Post by Van_Gogh on 2005-12-18
@Dave:
Yeah, I guess it's always easier to rehash what you've already learned than to use something new.

On a sidenote(and no comparison intended;)) , I saw a guy using Wordperfect 5.1 at uni the other day. Weird feeling seeing that beast again:p

---

### Post by xtacocorex on 2005-12-22
It should be noted that FORTRAN 77 has to be formatted correctly or else it won't compile, at least that's from my experience using F77 codes and trying to get them to work with F90 codes.

---

### Post by zugvogel on 2006-01-01
Many thanks to DaveRowell for asking this question and toojays for the answer! I have been going at this problem for weeks! Tried installing 3 different compilers (gfortran, ifort, g95) without success, before stumbling upon this thread!

Really, they should make one of the dependencies of the gfortran package, this build-essentials. It would have saved me (and I can see others) a lot of time.

And I would agree - Although you can apply much of what you learnt programming F77 to F90/F95, I think the experience will be much better using the latter.

---

