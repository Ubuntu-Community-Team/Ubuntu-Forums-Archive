---
title: "gcc compiling: segmentation fault (core dumped)"
date: 2007-11-02
forum: Packaging and Compiling Programs
---

### Post by Mittens on 2007-11-02
Hi Everyone,

As a linux uber-beginner, I've been running Ubuntu now for a couple of months, and in the last couple of days have begun compiling c code using gcc.  I'm able to compile my own c code and generate executables.

Simple executables will actually run properly, which is great, but other executables will only briefly run and then terminate with the following message:

"Segmentation fault (core dumped)"

Such errors are taking place with c code that I've previously been very productive with in the following operating environments: AIX, Sun, and Windows.  For this reason, I'm wondering if there might be something basic that I'm missing regarding compilation of c code using gcc on Ubuntu.  

Assuming for the moment that the code itself is fine (which I believe is the case, based on past successes in several other environments), does anyone know if there might be some typical error that linux newbies make that could cause the above type of error?  Might there be some kind of simple command I could enter to verify that my gcc install (including all libraries) is fully operational?  I compile simply by typing "gcc xxxxx.c -lm" - might there be another modifier I need to add to ensure proper compilation?

Keep in mind that I really am a linux beginner.  Until recently, I've clung most tightly to my very old Turbo C compiler (a PC compiler from the late 80's!) to generate executables for my personal scientific computing, but feel I need to move on (for one thing, array sizes seem to be incredibly limited in Turbo C).

Thanks,

Mittens


P.S.

FYI: Running gdb on a particular program that I've tested extensively in the past on other operating systems and hardware yields the following at the point of error:

"Program received signal SIGSEGV, Segmentation fault.
0xb7e0672d in fclose () from /lib/tls/i686/cmov/libc.so.6"

Not being a programming guru, I have no idea if this message offers a clue that might lead to the problem's resolution.  No line number is given in this gdb report.

---

### Post by geraldm on 2007-11-03
A segfault in the compiler is an introduction to programming.

The command line used is seriously lacking, or else the program can
only do very little.  Here are the blocks of what is expected on one 
line:

compiler name:  gcc
flags:  -Wall -I/usr/include -I. (etc)
objects and shared libraries: -L/usr/lib -lm -ldl
program:  xxxxxx.c
static libraries. (if any, usually none in linux, which favors shared)

flags:  you need to provide the path(s) to the headers used in your program.
libs: You need the big L (directory), and can then abbreviate the little
'el' for every library file that begins with "lib" in that directory.
For most programs using libraries, you will need libdl, which assists
loading shared libraries.
You do not need to use a Makefile, but learning that will save a lot
of typing.  In starting, just ignore compiler segfaults, and try to do
a little different next time, learning not to do as that happened. 

Good luck,
Gerald

---

### Post by Mittens on 2007-11-03
Hi Gerald,

Thanks very much for the hints!  I'll try a few additional command-line options, as you suggest (although my programs are actually quite simple despite their length, so additional command-line options may not be the solution).

Cheers,

Mittens

---

### Post by RAOF on 2007-11-04
1) It would be useful to actually see this code (if you're able to share it).
2) Backtraces are more useful when they include the entire call-stack (bt full), but I'd guess that you're passing in a NULL pointer into fclose().

---

