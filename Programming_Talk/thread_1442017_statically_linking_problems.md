---
title: "statically linking problems"
date: 2010-03-29
forum: Programming Talk
---

### Post by Houman on 2010-03-29
hello ;

I have been trying desperately to statically link against a library ; the program i am using is a sample program provided by the library and I keep getting an "undefined reference" error during the linkage process;

it is strange because this is the line i use for linking:

```

g++ -LCLAPACK  testlap.o -o ellipsefit -lm -llapack -lblas

```


this is the error i get:

```

testlap.o:testlap.c:(.text+0x13a): undefined reference to`dgesvd_(char*, char*, long*, long*, double*, long*, double*,double*, long*, double*, long*, double*, long*, long*)' collect2: ld returned 1 exit status

```

and when i do :

```

nm liblapack.a | grep dgesvd_

```

I get:

```

00000000 T _dgesvd_

```

so the symbol is there but doesn't get linked. I may be missing something here. I would appreciate any help;

Oh and the strange thing is that when i install this library via apt somehow it forces me to install the shared and the static libraries. In that case it links fine, but then if i remove the shared and static libraries and just copy the *.a files of the static libraries and put them in my local libs directory it doesnt work;

thank you 
H

---

### Post by dwhitney67 on 2010-03-29
> **Houman said:**
> 
Oh and the strange thing is that when i install this library via apt somehow it forces me to install the shared and the static libraries. In that case it links fine, but then if i remove the shared and static libraries and just copy the *.a files of the static libraries and put them in my local libs directory it doesnt work;

thank you 
H

A .a is an archive file, which typically represents a static library.  A file with the .so extension is a shared-object library.

I would recommend that you use the apt installer's version of the library.

Also, do you know whether the source for the library was written in C or C++?  You could possibly be dealing with a name-mangling problem (but this does not appear to be the case).

P.S.  When both the shared- and static-libraries are installed, and you wish to link with the latter, specify GCC -static option before you specify the library.

---

### Post by Houman on 2010-03-29
hi there

actually you were correct , it was a name mangling problem;

i fixed it by putting my header files in this:

```

 extern "C" {
#include "f2c.h"
#include "clapack.h"
#include "blaswrap.h"
 }

```

Also I had to change the order of the libraries in the makefile; its now:


```

LIBS=  -l$(TMGLIB)  -l$(LAPACKLIB) -l$(BLASLIB) -l$(F2C) -lm 

```

however now I try to compile it on windows (my code has to run on both :( ) it does not work. I downloaded the prebuilt windows binaries for this lib and when i compile it with my gnu toolchain on windows i get a very large number of errors like this:

```

Warning: .drectve `/DEFAULTLIB:"LIBCMTD" /DEFAULTLIB:"OLDNAMES" /EDITANDCONTINUE ' unrecognized

```

repeated many times

and also stuff like this:
```

./liblapack.a(./Debug/dgesvd1.obj):(.text[_dgesvd_]+0xc830): undefined reference to `_RTC_CheckEsp'
./liblapack.a(./Debug/dgesvd1.obj):(.rtc$TMZ+0x0): undefined reference to `_RTC_Shutdown'
./liblapack.a(./Debug/dgesvd1.obj):(.rtc$IMZ+0x0): undefined reference to `_RTC_InitBase'
./liblapack.a(./Debug/dorglq1.obj):(.text[_dorglq_]+0x78e): undefined reference to `@_RTC_CheckStackVars@8'

```

it keeps going for hundreds of lines;

anyways I fixed the compile issue on linux at least; thank you for your help;
H

---

### Post by Houman on 2010-03-31
Hi
Just letting whoever is having similar problems with building lapack on windows know how i solved the problem in the last post.
Turns out the precompiled binaries for lapack on their website are compiled with visual studio which inserts weird symbols in their linked binaries that depend on certain windows libraries, hence the millions of unresolved symbols.

Since i wanted this to compile with the mingw compiler, i ended up compiling the source of the library on windows using Cmake (there is a cmake specific zip file on their site) , and when you use cmake you explicitly state which compiler you are building for (mingw) and the resulting library files will link fine using mingw;

thats it :)

Houman

---

