---
title: "declarations from stdlib.h missing, compile failure c++"
date: 2011-03-16
forum: Programming Talk
---

### Post by LMHmedchem on 2011-03-16
I have a software package that I have both windows and linux versions of. I have made some changes to the win version, and am getting ready to port to linux. I decided to find my last linux version and re-compile it, since I have moved to Ubuntu 10.04. The code will not compile and I am getting the following.

```

src/printing2.cpp:594: error: ‘WEXITSTATUS’ was not declared in this scope
src/printing2.cpp:618: error: ‘WIFSIGNALED’ was not declared in this scope
src/printing2.cpp:619: error: ‘WTERMSIG’ was not declared in this scope
src/printing2.cpp:626: error: ‘WIFSTOPPED’ was not declared in this scope
src/printing2.cpp:627: error: ‘WSTOPSIG’ was not declared in this scope

```These are all functions that are decoared in wait.h or stdlib.h. These headers are installed, and I have installed the build-essential meta package, along with g++, gcc, and gfortran, and devel libs. I have compiled this exact src before, so something seems to have changed in my environment with the new Ubuntu. I put the same src on another linux box with Scientific Linux 5.2, and it compiles just fine.

I am a bit at a loss as to where to look for the issue. I assume that I am missing a dependency of some kind, or forgot to install a package when I installed 10.04. I don't spend all that much time in Linux, so I am more than a bit in the weeds at the moment.

I have attached a .zip with the make file, and the printing2.cpp src file that is giving the error, in case anyone wants to have a look.

Suggestions would be greatly appreciated.

**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by SledgeHammer_999 on 2011-03-16
In C++ when using C-standard libs you better include them this way:
Instead of **#include <stdlib.h>** you should write **#include <cstdlib>**. Repeat for all C includes: put 'c' in front of the name and exclude '.h'

Also most of the C functions live under the std namespace. Did you use that?

---

### Post by LMHmedchem on 2011-03-16
> **SledgeHammer_999 said:**
> In C++ when using C-standard libs you better include them this way:
Instead of **#include <stdlib.h>** you should write **#include <cstdlib>**. Repeat for all C includes: put 'c' in front of the name and exclude '.h'

Also most of the C functions live under the std namespace. Did you use that?As it happens, neither wait.h, or stdlib.h are included in the file that is failing to compile.

There is an #ifdef unix on the code block. That would imply that unix is defined by default in Ubuntu, but not Scientific Linux, since the SL compiles and also doesn't have the includes. Is there a way to determine what has been defined by default?

I tested on Ubuntu 9, and I got it to compile by adding wait.h. Is there any preference for which header to include, wait.h, or stdlib.h?

**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by MadCow108 on 2011-03-16
> **LMHmedchem said:**
> As it happens, neither wait.h, or stdlib.h are included in the file that is failing to compile.

There is an #ifdef unix on the code block. That would imply that unix is defined by default in Ubuntu, but not Scientific Linux, since the SL compiles and also doesn't have the includes. Is there a way to determine what has been defined by default?

I tested on Ubuntu 9, and I got it to compile by adding wait.h. Is there any preference for which header to include, wait.h, or stdlib.h?

**[COLOR=Navy]LMHmedchem[/COLOR]**

if you only need the stuff from sys/wait.h then only include that and not stdlib.h
Its always best to keep the number of includes small, it benefits compile time and makes it easier to get dependencies right (especially in headers including other headers)

---

### Post by LMHmedchem on 2011-03-16
> **MadCow108 said:**
> if you only need the stuff from sys/wait.h then only include that and not stdlib.h
Its always best to keep the number of includes small, it benefits compile time and makes it easier to get dependencies right (especially in headers including other headers)I will probably go ahead with wait.h, since that compiles and it makes sense to keep things lite.

Any idea why this compiles on SL without the include? Is there a way to determine if unix is defined by default under Ubuntu?

LMHmedchem

---

### Post by MadCow108 on 2011-03-16
As far as I know SL 5 uses gcc 4.1.2 (at least SL CERN 5.6 does)
there was a major reduction of unnecessary includes from the standard headers in gcc 4.3 which may be the reason.

---

### Post by LMHmedchem on 2011-03-16
I really only use gcc3, but it seems there is no way to install just gcc3 in ubuntu, without getting gcc4 along with it. In windows, I use gcc3 under cygwin, and things seem to work well. I use very basic functions for the most part, and keeping to version 3 has simplified things in windows quite a bit. At least mno-cygwin is still in gcc3.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

