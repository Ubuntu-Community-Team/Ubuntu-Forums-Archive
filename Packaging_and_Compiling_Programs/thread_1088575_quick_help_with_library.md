---
title: "quick help with library"
date: 2009-03-06
forum: Packaging and Compiling Programs
---

### Post by gafferuk on 2009-03-06
Hi, im new to lixux but not c programming.

Im trying to use The Synthesis ToolKit in C++ (STK) but im having trouble using it.

The IDE im using is geany. And im using the following includes;
#include <string>
#include <iostream>
#include <sstream>
#include <vector>

when i build im receiving errors like:
/usr/include/stk/include/Stk.h:56:18: error: string: No such file or directory

what library do i have to include to use these headers and what is the build command?

im using:
compile: gcc -Wall -c -D__LITTLE_ENDIAN__ "-I/usr/include/stk %f" -lstk

and for build im using;
gcc -Wall -o "%e" "-I/usr/include/stk/include" "%f" -lstk

Thanks for your time, much appreciated!!

---

