---
title: "Where's the debug function?"
date: 2007-07-21
forum: Programming Talk
---

### Post by w1nD on 2007-07-21
Hello everyone,

I am brand new to the world of Ubuntu, but I am interested in learning all the aspects of this wonderful OS.

I downloaded Geany and wrote a simple program, but I don't seem to find the Debug function for it! On my Windows Vista computer, I use Visual Studio 2005 and I debug my C++ programs, but I can't seem to find it on Geany.

Can someone tell me where it is, or recommend another program?

Thanks!

---

### Post by Paul820 on 2007-07-21
Geany doesn't have the debugger built in, to debug you will have to drop to the terminal to do that using gdb. You could try another IDE if you like, there is a sticky at the top of the programming section for recommended IDE's. Codeblocks is good, integrated with the gdb debugger so you can debug from within that. I have not really  used any other IDE, so if anyone can recommend another one with a debugger?

---

### Post by ddrichardson on 2007-07-21
I don't do much in the way of graphical programming, but gdb is useful.

---

### Post by vambo on 2007-07-21
gdb works like a dream under emacs. Just remember to compile with the -g flag

---

### Post by w1nD on 2007-07-22
Ok, so GDB it is.

How do I use it?

I mean, how do I access GDB? Do i have to type anything in the terminal?

I went and downloaded GDB and it said that I had a later version installed... So, where is this GDB in Ubuntu and how do i use it?

Thanks!

---

### Post by the_unforgiven on 2007-07-22
gdb is basically a command line general purpose debugger that is written/supported by the free software foundation.

For the following discussion, let's assume that the executable binary that your compiler generated is called HelloWorld (to represent the basic "Hello, World!" program).

To be useful, make sure your program is compiled with debugging symbols - i.e. until you're sure about your code, compile it with -g option to gcc. gdb can still allow you to debug the program, but it MAY NOT be able to give you high-level language support (like C statements etc.) - you'd end up going to the assembly level to debug the code.

To start debugging, on a command prompt just type:```
$ gdb /path/to/HelloWorld
```
It will show gdb license and drop you to the **gdb>** prompt. Now, at this prompt, you enter various commands for the debugger, like to set a breakpoint at the entry of main(), you do:```
gdb> b main
```
To run the program, you tell gdb to run it with:```
gdb> r
```command.
To step through the code (one source line at a time), you do:```
gdb> n
```
To step INTO a function, you do:```
gdb> s
```
To simply get help in the debugger, you do: ```
gdb> help
```
etc. 
More details are available in the [GDB Quick Reference card]("http://refcards.com/docs/peschr/gdb/gdb-refcard-a4.pdf").

HTH ;)

---

### Post by w1nD on 2007-07-22
Wow, thanks!

That sounds complicated at first, but it seems to be better than Visual Studio 2005 in a way.

Thanks again!

---

### Post by Mathiasdm on 2007-07-22
And if you prefer to work graphically, give 'Eclipse' a try. It supports (through plug-ins) lots of different programming languages.

---

### Post by PointSource on 2007-07-22
There are also a few standalone GDB frontends. I have personally tried kdbg, nemiver (has bugs) and ddd.

Anjuta also has integrated debugging.

---

### Post by rahul.gupta on 2007-07-23
> **Mathiasdm said:**
> And if you prefer to work graphically, give 'Eclipse' a try. It supports (through plug-ins) lots of different programming languages.

You'll need to install CDT plugin in order to get get c++ support.
You can also try Anjuta, though my personal preference is eclipse.

---

### Post by Paul Miller on 2007-07-24
I usually do most of my debugging with print statements, or whatever the equivalent is in the language you're working in. :-)  Basically all gdb and other debuggers do anyway is allow you to stop and inspect the values of variables in your program, which is something you can do by inserting a print statement at the appropriate place.

---

### Post by the_unforgiven on 2007-07-24
> **Paul Miller said:**
> I usually do most of my debugging with print statements, or whatever the equivalent is in the language you're working in. :-)  Basically all gdb and other debuggers do anyway is allow you to stop and inspect the values of variables in your program, which is something you can do by inserting a print statement at the appropriate place.
The problems with print debugging approach:
o. Requires recompilation to disable prints once you're done with debugging.
o. Goes too deep in the code - i.e. you manually have to keep adding prints everywhere; the chances of you missing a print at a required location are pretty high.
o. It gets quite cumbersome to manage - you cannot selectively disable prints; you can either enable them all or disable them all.
o. You cannot **inspect** the state of data-structures - parts of the DS that you haven't included in the prints go un-noticed, where in fact the problem could lie in corruption of that part.
o. Can be quite confusing for multi-threaded programs - to the point of becoming useless.

As for the compiling with -g (including debugging symbols), the debugging symbols can be removed without recompilation by using the **strip** utility.

IOW, prints are good and easy for smallish programs, but it's totally useless for anything more than about five hundred lines of code.

---

