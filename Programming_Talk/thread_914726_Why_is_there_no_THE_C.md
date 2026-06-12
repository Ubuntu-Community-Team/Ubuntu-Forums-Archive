---
title: "Why is there no THE C?"
date: 2008-09-09
forum: Programming Talk
---

### Post by Erdaron on 2008-09-09
Given that there are international standards defining the C language, why isn't there some centralized body (similar to Python Software Foundation) that in charge of making standard compilers and maintaining standard libraries?

While this question is borne out of frustration of trying to compile something on a 64-bit Windows machine, I'm also genuinely curious at the state of things. C seems like it is even more important than Python, and there's an ISO standard for it, yet its actual maintenance seems a lot more disorganized.

---

### Post by cb951303 on 2008-09-09
Because Python is an interpreted language and C is not. Interpreted languages are *a lot* more easier to make it work on different platforms. (EDIT) There is ofcourse an ISO standart for c, look for C89(ansi) C99. But to be honest I don't know of a compiler that supports C99 fully

---

### Post by pansz on 2008-09-09
IMO GCC is essentially "the C compiler" 

MS Windows seems to have completely abandoned C since MS Visual C++ cannot compile C code at all. (try compile some file which named foobar.c). is that clear?

AFAIK Windows is the *only* platform which do not have a *standard* C compiler. 

anyway you can still use gcc in Windows.

---

### Post by samjh on 2008-09-09
> **Erdaron said:**
> Given that there are international standards defining the C language, why isn't there some centralized body (similar to Python Software Foundation) that in charge of making standard compilers and maintaining standard libraries?
Firstly, the PSF holds intellectual property rights to Python, its license and trademark.  No-one holds intellectual property rights to the C programming language or its name.

Secondly, the C programming language is standardised by ISO.  Python is not standardised by anyone, but contributions to the Python language and its "standard" libraries are controlled by PSF.  This is similar to Java and how it is controlled by JCP.  The PSF can do this by virtue of their rights over the Python trademark and license.  No-one has the same legal stranglehold over C, therefore a central organisation that controls C compilers and standard libraries will be without teeth.

Thirdly, because the C programming language is standardised by ISO in a publicly-viewable document(s), and because there is no legal rights holder to the language itself, the onus falls squarely on the developers of the C compilers, standard libraries, and associated tools, to ensure their products are ISO standard-compliant.  Same for the users of the language: pick a vendor who creates ISO standard-compliant C tools.

As for difficulties related to cross-compiling between different architectures using the C language, Python unfortunately suffers from similar problem: making Python programs work across different implementations.  CPython (the usual flavour of Python) differs somewhat from Jython (Python on JVM) and IronPython (Python on the .NET Framework).  When you switch the runtime environment for any programming language, problems are inevitable.

> **pansz said:**
> IMO GCC is essentially "the C compiler" 

MS Windows seems to have completely abandoned C since MS Visual C++ cannot compile C code at all. (try compile some file which named foobar.c). is that clear?

AFAIK Windows is the *only* platform which do not have a *standard* C compiler. 

anyway you can still use gcc in Windows.Visual C++ compiles C code fine, actually.

And what do you mean by Windows being the only platform without a standard C compiler?  You can use MinGW, ICC, TCC, GCC, Digital Mars, and more.  As far as I know, all of them are compliant with at least ISO C89, and most - if not all - of C99.  Visual C++ is C89 compliant, but not C99 compliant (they are considering C1x compliance).

---

### Post by sonofusion82 on 2008-09-09
the ISO/ANSI C standards dictates mostly the language part only and leaves the implementation up to different implemetations. problem usually happens when some compilers doesnt fully follow the standard and also variation in implementation details not covered by the standard.

it is probably similar to the web standards that is done by the W3C and there is not THE WEB BROWSER and web developers are having the pain to get their codes to work on different browsers

on the other hand, for python, CPython is the de-facto standard as it is maintained by Guido who is THE creator of python.

---

### Post by pansz on 2008-09-09
> **samjh said:**
> 
Visual C++ compiles C code fine, actually.

And what do you mean by Windows being the only platform without a standard C compiler?

As far as I know the only way to compile a C file in Visual C++ is to change the filename foobar.c into foobar.cpp. And then the C source must be C++ compatible, there is no C99 feature in Visual C++, not even the simplest like "stdint.h"

We know "not all C code can be compiled as C++ code".


What I'm saying "standard" compiler means: you expect the users on that platform will almost alwlays compile the code with that compiler.

On linux, we could expect users will almost always compile their C codes with gcc, couldn't we?

And what do you expect users will use to compile a C code on Windows? I don't know, since Visual C++ will not compile C code and it has absolutely no C99 support.

---

### Post by samjh on 2008-09-09
> **pansz said:**
> As far as I know the only way to compile a C file in Visual C++ is to change the filename foobar.c into foobar.cpp.

I can't understand why you have problems compiling C code in Visual C++.  I've compiled C code using Visual C++ 6 through to 8, without dramas.

True that VC++ doesn't have C99 support.  But frankly, C programming is nowhere near as popular on Windows as it is for Unix/Linux/BSD.  Microsoft has already blogged that there is not enough consumer demand for C99 compliance on VC++, although there is limited C99 features supported, and consideration is being given for C1x support in the future.

I'd actually expect Windows users to use MinGW to compile C code on Windows.  It's by the most popular, alongside the Cygwin environment.

---

### Post by pansz on 2008-09-18
I had tested in Visual C++6, 2003 and 2005, all of them cannot create *.c file and cannot compile them. So it is probably that Microsoft had disabled these "features" in the localized version?

Anyway, that's is not a big issue for me, if VC++ cannot compile C code or cannot support C99, just don't use it. The problem is that cygwin shell environment is much slower than Linux. Especially when compiling programs:

I compiled our own project:
Compile in Windows cygwin: 2.5 hours
Compile in Linux: 0.5 hours
Compile in Windows Vmware Linux: 0.6 hours

cygwin is slower than Linux-in-a-virtual-machine

---

### Post by Erdaron on 2008-09-19
> **pansz said:**
> I had tested in Visual C++6, 2003 and 2005, all of them cannot create *.c file and cannot compile them. So it is probably that Microsoft had disabled these "features" in the localized version?

Anyway, that's is not a big issue for me, if VC++ cannot compile C code or cannot support C99, just don't use it. The problem is that cygwin shell environment is much slower than Linux. Especially when compiling programs:

I compiled our own project:
Compile in Windows cygwin: 2.5 hours
Compile in Linux: 0.5 hours
Compile in Windows Vmware Linux: 0.6 hours

cygwin is slower than Linux-in-a-virtual-machine

Have you compiled the same project using MinGW? Since it's a direct native port of gcc to Windows, it might work better?

Another point brought up here seems strange - how come there are compilers that implement only some of C99 features? This seems contrary to having a standard, if people simply have their way with it.

---

### Post by cb951303 on 2008-09-19
> **Erdaron said:**
> Have you compiled the same project using MinGW? Since it's a direct native port of gcc to Windows, it might work better?

Another point brought up here seems strange - how come there are compilers that implement only some of C99 features? This seems contrary to having a standard, if people simply have their way with it.

exactly, that's bothering me too. c99 has some very nice futures like variable length arrays. The last time I checked none of the compilers had this feature.

---

