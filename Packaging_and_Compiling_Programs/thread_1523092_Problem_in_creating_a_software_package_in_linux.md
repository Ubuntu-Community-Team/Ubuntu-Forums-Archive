---
title: "Problem in creating a software package in linux?"
date: 2010-07-03
forum: Packaging and Compiling Programs
---

### Post by jeremy28 on 2010-07-03
Hi all

I have a project that includes a file called “main.cpp” that the “main” function is defined in it and also has a series of header and source files that each one has defined a special class to do a special task! 
Now, I want to make a software package for this project;

Frankly, this is my first experience! 
Thus, I want to write a Makefile that compiles the project and runs it;

I’ve created a folder named “project” containing all of project’s files and folders. Inside it, I have:

1 - a folder named “MainSrv” containing “main.cpp” file.
2 - a folder named “include” containing all of header files. 
3 –a folder named “lib” containing all of object files(.o), shared objects(.so) and archive files(.a). 
4 –a folder named “src” containing all of “.cpp” files.
5 –a folder named “config” containing “config.cfg” file of the project.

At the beginning of “main.cpp” file, I should include some of that header files. I want to know how should be the include operation? 
For example, one of them is “ptsocket.h”, I do so for including it:
```
#Include "include/ptsocket.h"
```
But I know it is wrong, because my “main.cpp” file is in a folder named MainSrv and when I could do so that the “include” folder was inside this folder (MainSrv) and beside the main.cpp!

What I want, is that I return back from “MainSrv” folder(which gets into “project” folder) and there, from “include” folder, add the ptsocket.h file to the program. But I don’t know how could be this task in “#include” directive?

Is this correct in your opinion:
```
#include “../include/ptsocket.h”
```
If so, how many should be the dots number (2 or 3)?

(I mean, I have problem with applying file paths in #include for each .cpp file!)

Also, I want to write a Makefile to compile these files and also to install the produced libraries in the system (so that, these path definitions are done in it…)

I ask you help me with that or introduce me a complete document to build a software package in linux and correct setting of a Makefile according to it.

TIA.

---

### Post by SevenMachines on 2010-07-05
personally i tend to have headers and source together, for example> 
src->[INDENT]SomeClass.h
SomeClass.cpp

somesubdir->[INDENT]SomeOtherClass.h
SomeOtherClass.cpp
[/INDENT][/INDENT]so SomeClass.h might have
#include "somesubdir/SomeOtherClass.h"

ie, relative paths in a source subtree. you could in your case do
#include "../includes/SomeClass.h"
or you could add the 'includes' directory to the compiler options with -I, i'm not sure which way is the 'better one'

For makefiles i'll default to my standard link to a basic tutorial :) Explains things better than i ever can!
[http://mrbook.org/tutorials/make/](http://mrbook.org/tutorials/make/)

---

