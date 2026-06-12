---
title: "Kdevelop not compiling / debugging."
date: 2012-10-08
forum: Programming Talk
---

### Post by zedx555 on 2012-10-08
So I have a project in Kdevelop4 with cmakelists.txt on the main folder but it goes to build in the build folder and says 

make: *** No targets specified and no makefile found.  Stop.
*** Failed ***

I can build in terminal using cmake -> make but I can't do it nor debug in kdevelop.

---

### Post by Zugzwang on 2012-10-09
I have no clue about cmake, but here is my guess:

The file should be called "CMakeLists.txt" and not "cmakelists.txt". If renaming the file does not fix the problem, try compiling your project from the terminal. This way you can distinguish between IDE and CMake problems, which should narrow your search for a solution.

---

