---
title: "Ubuntu gcc doesn't compile RHEL developed C++ code"
date: 2010-04-14
forum: Programming Talk
---

### Post by mjobrien on 2010-04-14
Hi everyone, this is my first post since most of the time I've been able to find answers in previous threads (Thanks to all!)

I just put Ubuntu 9.10 on my work machine, and I am new to Linux overall.  I am trying to compile code that was developed and previously built at work on Centos 5.4 (both on 32 & 64 bit machines).  I can build everything just fine if I login into a machine at work, but when I try to build on my work machine (that I setup), off site, and I get errors.  The errors include problems with 

uint
exit()
sort (vector sort)
memset
memcpy
and some others, perhaps that I cannot recall.

I was able to fix these problems through adding header files

string.h
types.h
(others that I don't recall),

however I feel this is not the best solution since whenever changes are done by others at work, I may run into compiling issues again.  I feel like the problem must be with my gcc configuration, or something of that sort.  If anybody has any ideas, I would be very appreciative.  More information:  I use omake 0.9.8.5 for both work and offsite builds.  At work I have gcc 4.1.2, and on my Ubuntu machine I have gcc 4.4.1.  Is this the reason for my problem?  Are newer versions of gcc setup to be more slimmed down, and don't include many of the previously included header files?  Or, do you think it is configuration of omake that gives the problems?

Thanks in advance!
Mike

---

### Post by lisati on 2010-04-14
Just to clarify, are you working with C or C++? Some of the examples you have given look more like C to me than C++.

---

### Post by mjobrien on 2010-04-14
Umm...c++, but a lot of the code is c code for better future portability to cuda.  I'm not sure if that sufficiently answers your question ;o)

---

### Post by falconindy on 2010-04-14
I'm wondering how you were able to compile **without** those headers. CentOS and Ubuntu are both gcc/glibc based distributions. In the case of differing compilers and/or cross developing, this is what preprocessor macros are for.

---

### Post by MadCow108 on 2010-04-14
What kind of errors are you encountering?
I guess the problems are related to poor adherence to the c++ standard of your code and not to a wrong configuration.
increasing gcc and libc versions often remove deprecated old functionalities and headers.
So bad/old code may stop compiling in newer versions.

It is best to fix these problems in the code and educate your coworkers in writing standard code.
This includes using the right headers.
To include C headers in C++ you remove the extension from the name and a c in front.
e.g. string.h gets cstring

also always include the system headers after the project related headers, this helps finding missing header dependencies.

---

### Post by mjobrien on 2010-04-14
Thanks for the tips.  I am not sure how it was able to compile properly before w/o the headers....this is why I perceived the problem to possibly be configuration dependent.  Unfortunately, the code lead is the one that developed most of the (often frustrating) code, with his seemingly unique coding style (or, perhaps it is just more of a "c coding style").  It is unlikely that this will ever change since I'm just an intern, and the code lead is pretty set in his ways  ;o)  Thanks though for the advice.

---

### Post by lisati on 2010-04-14
Another thing: if it's mainly C++ that you're using, I'd suggest using g++ instead of gcc.

---

### Post by mjobrien on 2010-05-10
I know I posted this a long time ago, but I recently revisited the problem, and I found the cause.  The best solution is to find the appropriate headers, and add them in manually.  This will allow for better portability.  But, an alternative solution is to make sure you compile using gcc/g++ 4.1.  The problem seems to be that somewhere in the transition from version 4.1 -> version 4.4, backward compatibility requirements were left out, causing things like "uint", "(vector) sort", "memset", "memcpy" (etc), "int abs(int)", as well as other old functionality that was automatically included to be left out.  You can either find the appropriate header files to be included, such as:

uint --> found int sys/types.h
mem* --> found in string.h
---- etc ----

Or dl gcc/g++ 4.1, and force your build utility to use this for compiling (rather than the latest version).

Cheers!
Mike

---

