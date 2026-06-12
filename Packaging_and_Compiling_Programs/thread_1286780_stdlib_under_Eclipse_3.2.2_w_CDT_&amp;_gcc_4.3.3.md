---
title: "stdlib under Eclipse 3.2.2 w/ CDT &amp; gcc 4.3.3"
date: 2009-10-09
forum: Packaging and Compiling Programs
---

### Post by uiberto on 2009-10-09
Hi,

I'm working on a programming project with a partner. I'm running Eclipse 3.2.2 w/ CDT & gcc 4.3.3. I think he's running a recent version of Xcode on a Mac.

When he sends me a piece of code, he often uses functions from a few standard libraries (stdlib.h, limits.h, string.h) without ever including the library. It compiles fine on his box, but I have to manually include the libraries in the appropriate file.

```

Building file: ../code.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"code.d" -MT"code.d" -o"code.o" "../code.cpp"
../code.cpp: In member function ‘char Code::getAminoAcidCode(int, int, int)’:
../code.cpp:69: error: ‘exit’ was not declared in this scope
make: *** [code.o] Error 1

```

I found a page discussing that gcc 3.4.x and earlier used to include stdlib.h as a dependency when you included iostream and that this was changed in gcc 4.?.?. Maybe he has an old version of gcc? Will check.

He said his Xcode does not automatically link any libraries. He also said he's tested this code on a variety of platforms over the past 5 years. Maybe Eclipse is not linking stdlib, limits, string, etc correctly. 

I haven't programmed in a few years, but something seems strange.

Any thoughts?

Thanks,

uiberto

---

### Post by MadCow108 on 2009-10-09
some compilers include some standard headers and libraries by default others don't

so you should always include everything that is needed even when it is not required to do so by your compiler. This eliminates these kind of problems.
So get your partner to write proper portable code would be the best solution.

you could also use the -include flag of gcc to always include the missing headers without modifying the source files. but the latter is recommended.

---

### Post by uiberto on 2009-10-12
Thanks for the helpful reply.

---

