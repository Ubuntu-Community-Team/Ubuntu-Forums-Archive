---
title: "Newb to Linux Programming, Need Help"
date: 2008-01-13
forum: Packaging and Compiling Programs
---

### Post by Tristanm1 on 2008-01-13
I am trying to make the switch over to Linux when it comes to programming. Being only a beginner programmer myself, I have quickly become lost. I can write code in Geany just fine. When I get to compiling, I can't figure out how to compile by command line, and when I compile through Geany, I get a .o file that I can't do anything with. I can't exactly do much programming if I can't compile my programs, or run them.

I am working with C++ at the moment, but will move to working with C when I set up a PSP Dev environment.

---

### Post by tanderson on 2008-01-14
Here is a link to a starting point with the command line. 

[http://en.wikibooks.org/wiki/C++_Programming/Examples/Hello_world](http://en.wikibooks.org/wiki/C++_Programming/Examples/Hello_world)

C/C++ app building is a two step process compiling and linking. The output file of the compiler have a .o extension for object code. These are not executables, but are meant to be fed into the linker which will generate the executable. Most modern gui's will have a build command that will let you do both compile and link in one command.

---

### Post by Tristanm1 on 2008-01-14
Alright, so is there also a way to compile source code into a Windows binary in Linux, or do I need to dual boot for that?

---

### Post by pedro_orange on 2008-01-15
Some compilers allow you to compile object files for other platforms, these are generally referred to as cross-compilers. 
GCC uses ELF, while Windows uses something else. So you may need to invest some time looking for a new compiler.

The problem with porting code over Operating systems is that the libraries are different. Generally with standard libraries such as math, algorithm etc this is not an issue.
But when you are talking about graphics and other sophisticated operations then these tend to be less standardised and highly variable over differing operating systems.

---

### Post by Tristanm1 on 2008-01-17
Well, if cross platform libraries such as Allegro and SDL are used, there shouldn't be much of a problem... theoretically...

---

