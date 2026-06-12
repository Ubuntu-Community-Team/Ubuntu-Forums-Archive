---
title: "How to get g++ and gcc to work?"
date: 2005-07-29
forum: Programming Talk
---

### Post by kalle314 on 2005-07-29
I used Synaptic to download and install the packages I thought I would need:

gcc              (4:3.3.5-1)
g++            (4:3.3.5-1)
libg++27     (2.7.2.1-19)
libgcc1         (1:4.0.0-7ubuntu...)

and some other packages that were included automatically.

The helloworld program works fine for g++, but for gcc I got
[SIZE=1]
"/tmp/cc0f2Ifm.o(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status".[/SIZE]

I have two larger c++ programs that can be compiled by gcc and g++ in solaris and cygwin (and runs fine) , but neither of these programs can be compiled now (both gcc and g++ fails to compile.)

[SIZE=1](For example, I get parsing errors and 
"/usr/include/langinfo.h:48: error: `__LC_TIME' was not declared in this scope
/usr/include/langinfo.h:48: error: enumerator value for `ABDAY_1' not integer
   constant
/usr/include/langinfo.h:241: error: `__LC_COLLATE' was not declared in this
   scope".)[/SIZE]

What shall I do?

---

### Post by Zelut on 2005-07-29
If you need those libraries for compiling try using #sudo apt-get install build-essential.  Those are all the packages needed for building, compiling, etc.  Hope that fixes your problem.

You may need to remove the few that you've already installed.

---

### Post by kalle314 on 2005-07-29
Thanks for the quick answer :) 

I did "sudo apt-get install build-essential", but I still get the same compilation errors :-? 
gcc produces errors when I'm trying to compile helloworld.
g++ manages to compile helloworld, but fails for a bigger program (a rather easy one, only a header file and a .C-file.)


[SIZE=1](When I try to remove any of the packages I installed , Synaptic warns that I am about to remove essential  packages, which might damage the system.) edit: solved.[/SIZE]

edit again: Now gcc compiles helloworld without problem.

---

### Post by kalle314 on 2005-07-30
Most of my problems are solved now - there wasn't a single easy solution, but I had to do many small different things, like

* downloading packages with headers that were missing, like Xutil.h, Xlib.h, Xatom.h,...
* link to headers that the compiler didn't find. Maybe this could be done once and for all? I did it by swiches in the makefile anyway.
* writing ./a.out instead of a.out when running
* writing "sudo make" instead of only "make" - otherwise files  (located in my own home directory) that needed to be written to couldn't be accessed.

Are there more things to think about when compiling c++ in ubuntu?

---

### Post by grofaz on 2005-07-30
What a pain in the butt! I still can't get anjuta to create a single wizard project, let alone something I wrote up from scratch. I wish somebody would package it up into one neat bundle so all you have to do is install it and go. ](*,)

---

