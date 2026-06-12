---
title: "header files and linking?"
date: 2009-07-29
forum: Programming Talk
---

### Post by iochinome on 2009-07-29
hey guys, so i have a pretty long program that i just realized i need to organize better. so far, since i never really learned about header files, i have just made the program of 3 source files, one containing the main() function, and defining all the other functions i need on the other two source files, including them at the top of the main file with

(in main.cpp)
#include "source1.cpp"
#include "source2.cpp"

i hit some roadblocks with scope, though, and thought that now was a good time to look into it. i have read a bit on the subject, but there is one thing that i dont understand. i made header files, source1.h and source2.h respectively, each of which contain declarations of the variables, functions and structs described in the cpp files. i include these in the main.cpp with

#include "source1.h"
#include "source2.h"

the actual description of what, say, the functions do, though is contained in the .cpp files though, so none of my function calls have any meaning. how, without making a makefile, does one go about doing this? all i want is to be able to use the functions declared in all 3 files in any of the others. thanks!

---

### Post by jpkotta on 2009-07-30
> how, without making a makefile, does one go about doing this? all i want is to be able to use the functions declared in all 3 files in any of the others. thanks!

That sounds like bad organization.  Your #includes should look like a tree (really, a directed acyclic graph), not a spiderweb.  As in, specific.cpp can #include general.h, but general.{h,cpp} shouldn't depend on specific.{h,cpp}.

You stop the build at assembling, and leave linking till the end (-c).  make will automate most of this, you should look into it.
```

g++ -c source1.cpp -o source1.o
g++ -c source2.cpp -o source2.o
g++ -c main.cpp -o main.o
g++ -o main main.o source1.o source2.o
```

---

### Post by abhilashm86 on 2009-07-30
> **iochinome said:**
> 
(in main.cpp)
#include "source1.cpp"
#include "source2.cpp"

 all i want is to be able to use the functions declared in all 3 files in any of the others. thanks!

do u mean that even you have to execute some function through header files source1.h?? i think this is not function of header files.......
header files are used to function defnition, variables and class declarations...........

---

