---
title: "compiling in c++"
date: 2011-10-18
forum: Programming Talk
---

### Post by crimscx on 2011-10-18
i want to start programming in c++ for linux (ubuntu) but if i compile..it gives me a .exe file, obviously thats not native to linux soo..what executeable file IS native to linux and how do i output a c++ compiler so that it will make that file when compiling..i know you can make a windows console application and make it run by the terminal..but like i said..not a .exe, so am i learning the wrong language (non native to ubuntu even though i heard the linux kernal was made from c) or is there a way to output a native file to double lick and run..

---

### Post by crimscx on 2011-10-18
when i write a source code in c++ on ubuntu (NOT A CONSOLE APPLICATION) and i go to compile it, it will make a .exe file..where do i go from there to make it to where i can run it on linux..i dont mean wine..for example people make c++ software turn it into .deb and post it, how do i make the c++ (.exe file) executable like everyone else has? when i download software ud think it wouldent work being coded in c++ but it does..like i said..how do i make the c++ .exe file executeable and not a console app..(terminal will read executeables files)

---

### Post by Bachstelze on 2011-10-18
.exe files are on Windows only. Linux (and UNIX in general) executables can have any name, but generally have no extension. To compile C++ code on Linux, use a C++ compiler like g++, it will turn your source files into a Linux executable.

---

### Post by closingBrace on 2011-10-19
Hi crimscx,

As far as I know, there are no way to build a Linux executable using Microsoft Windows. If there is a way, I don't know about it (and I don't want to know about it anyway).

So, first of all, you will need to install Linux on your computer (or on a virtual computer, see [https://www.virtualbox.org/](https://www.virtualbox.org/) or [http://www.vmware.com/](http://www.vmware.com/)). I think Ubuntu can be a good distribution to write and compile C++ programs.

Then, depending on your personnal preferences, you will be able to use a C++ compiler which will create Linux executables : Eclipse CDT (see [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)), gcc (see [http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)) or any other C++ compiler for Linux (if you find one).

Have a nice day.

---

### Post by mörgæs on 2011-10-19
Moved to Programming Talk.

---

### Post by cgroza on 2011-10-19
Could you show us the command you use to compile your code?
Try to cd to the directory and execute the resulting file:
```

cd path/to/dir
./executable.exe

```In Linux, you can end executables in .exe too because file extension has little to no importance.
And yes, it is possible to compile a Windows executable in Linux using a cross compiler. But I doubt you are actually doing that.

---

### Post by Zugzwang on 2011-10-20
Here's my guess:

@OP: Is it possible that you are programming C# and not C++? In the former case, .exe extensions are quite common. Try to run them using the command "mono <yourfile.exe>".

If not, please tell us which compiler you used.

---

### Post by deloquencia on 2011-10-20
> **crimscx said:**
> [...] how do i make the c++ .exe file executeable and not a console app..(terminal will read executeables files)

Just compile the source code with the GNU C/C++ Compiler (gcc).

In general if you like to code an application which input and output won't take place in the console you can use a Framework - a collection of reusable libraries with graphic user interface capabilities. 

With Linux and C/C++ you've got plenty, like Xlib, Motif or Lesstif, GTK+, QT and wxWidget. Just choose one Framework, start study the API and finally code what ever you like to code....

---

### Post by kaspar_silas on 2011-10-21
Very very simple demo

First install g++ if you haven't already done this. 
From the terminal:
**sudo apt-get install build-essential**

Then make a text file called Demo.cpp and add this text
```
#include <stdlib.h>
main()
{ 
    system("gedit");
}
```

then in the terminal naviagate to the Demo.cpp folder and type: 
**g++ Demo.cpp**

you should now have a file called a.out if you double click a text editor will start.

---

### Post by crimscx on 2011-10-22
1. can you program using c++ and make native linux applications?
2. is there a guide on how to do this? notice i said make a program..in c++..native to linux
3. incase theres no guide, can you explain how too? :mrgreen:

---

### Post by lisati on 2011-10-22
Threads merged. The OP has asked some questions about compiling C++ programs for Ubuntu in separate threads and does not appear to have been back to the original threads to read the replies.

---

### Post by karlson on 2011-10-22
> **crimscx said:**
> 1. can you program using c++ and make native linux applications?

Not sure what it means but compiling a C++ application on Linux if successful would make it native won't it?
> 
2. is there a guide on how to do this? notice i said make a program..in c++..native to linux

C++ tutorial might take a look at [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)
If something else you might want to clarify.
> 
3. incase theres no guide, can you explain how too? :mrgreen:
How to write C++? or compile?

---

