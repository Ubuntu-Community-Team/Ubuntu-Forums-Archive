---
title: "[SOLVED] compiled file"
date: 2008-04-04
forum: Programming Talk
---

### Post by StOoZ on 2008-04-04
I have a header file called 'algo.h' and all its implementation is in a file called 'algo.cc'.

is it possible to make the 'algo.cc' file compiled which then no-one can change its values nor to see what is inside?
if so, how do I do this?

---

### Post by Zugzwang on 2008-04-04
> **StOoZ said:**
> I have a header file called 'algo.h' and all its implementation is in a file called 'algo.cc'.

is it possible to make the 'algo.cc' file compiled which then no-one can change its values nor to see what is inside?
if so, how do I do this?

You can't prevent anyone from disassembling your code. You can only make that hard to do. ;-)

Also, you might get portability issues. For example you can't take an object file compiled for 32bit machines and link it to 64bit code (ok, *maybe* you can, but the errors the customers get without setting their compiler/linker options accordingly might scare them). At least when using this approach, you can't be sure that it works everywhere.

---

### Post by StOoZ on 2008-04-04
ok, but how I do it?
I know the consequences , and I just want to do it, for educational purposes only.
most of the packages that I use, are like that.

---

### Post by smartbei on 2008-04-04
You can comile to a lib (.a) file or to a dll, depending on your platform, after which, for all intents and purposes, no one can see what is inside. Customers will then be able to link with your library in order to use it.

You will, as Zugzwang mentioned, need to compile the file for several platforms so that people can download the one that fits them best.

---

### Post by StOoZ on 2008-04-04
if I understood you correctly, I can combine that algo.cc to a lib file (.a) , since im using linux, and supply it with the header file?

---

### Post by Tomatz on 2008-04-04
> **StOoZ said:**
> I have a header file called 'algo.h' and all its implementation is in a file called 'algo.cc'.

is it possible to make the 'algo.cc' file compiled which then no-one can change its values nor to see what is inside?
if so, how do I do this?

Go ask on the microsoft forums bahhh!

:lolflag:

---

### Post by StOoZ on 2008-04-04
what does it have to do with microsoft? there are many sources in linux which are consisted of compiled code, I just want to know it for my knowledge.

---

### Post by Tomatz on 2008-04-04
> **StOoZ said:**
> what does it have to do with microsoft? there are many sources in linux which are consisted of compiled code, I just want to know it for my knowledge.

Most FOSS is released as source. Why not do that then people/you can just make packages for different distro's (or people can just compile).

Unless you have something more sinister in mind  :twisted:

---

### Post by StOoZ on 2008-04-04
As I already mentioned, I want to know for educational purposes only.
If I would have wanted to do something that no-one can see, I would have done that in windows , its easy to do it in windows (compiled code...exe's dll's etc)

---

### Post by WW on 2008-04-04
To distribute the compiled code, why not just make algo.h and algo.o available?  This will only work for someone using the same compiler and computer architecture as you, but that is basically true whenever you want to distribute a precompiled binary.  You may already know this, but just in case: to create algo.o, use a command like this:
> 
$ g++ -c algo.cc


Tell your users to download the files, put them in the same directory as their main program,  and compile, link, and run their program with commands like this:
> 
$ g++ -c user_main.cpp
$ g++ user_main.o algo.o -o user_main
$ ./user_main

user_main.cpp should contain the line **#include "algo.h"**.

You could also create a "statically linked" library, but if you have just one file, I don't see why you need to.  If you must, you could do this.  Compile your file and create the .a file with the commands:
> 
$ g++ -c algo.cc
$ ar rs libalgo.a algo.o

Now you have a file called libalgo.a.  Tell your users to put this file and the header in the same directory as their main program,  and tell them to comile and link their main program with either this:
> 
$ g++ -c user_main.cpp
$ g++ user_main.o libalgo.a -o user_main

or
> 
$ g++ -c user_main.cpp
$ g++ user_main.o -L. -lalgo -o user_main


---

### Post by StOoZ on 2008-04-05
thanks a lot! , exactly what I was looking for.

---

