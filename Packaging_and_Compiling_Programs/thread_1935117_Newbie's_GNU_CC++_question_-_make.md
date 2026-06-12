---
title: "Newbie's GNU C/C++ question - make"
date: 2012-03-03
forum: Packaging and Compiling Programs
---

### Post by chenxinghao on 2012-03-03
I am new with Ubuntu and C++ programming. I installed Ubuntu 11.10 in Jan. of 2012 and and installed GNU C/C++ compilers shortly. I then migrated my old C codes programs from years ago on Sun Microsystems' Solaris to my Ubuntu box and managed to compile (using the gcc GNU C compiler) these old C codes with only a few changes. I then coded a few lines in C++ and compiled them with the g++ GNU C++ compiler. However, I noticed the makefile's behavioral difference between compiling C codes and compiling C++ codes.

For the C codes, my makefile looks like this:

LDFLAGS = -lm
CC = gcc
CFLAGS  = -O4

OBJS =     faultgen.o \
    init_faultgen.o \
    getfilenames.o \
    readckt.o \
    init_storage.o \
    checkclock.o \
    init_node.o \
    genfault.o

faultgen: $(OBJS) faultgen.h
    ${CC} ${CFLAGS} -o $@ $(OBJS) ${LDFLAGS} 

and the compilation message outputs are like these:

gcc -O4   -c -o faultgen.o faultgen.c
gcc -O4   -c -o init_faultgen.o init_faultgen.c
gcc -O4   -c -o getfilenames.o getfilenames.c
gcc -O4   -c -o readckt.o readckt.c
gcc -O4   -c -o init_storage.o init_storage.c
gcc -O4   -c -o checkclock.o checkclock.c
gcc -O4   -c -o init_node.o init_node.c
gcc -O4   -c -o genfault.o genfault.c
gcc -O4 -o faultgen faultgen.o init_faultgen.o getfilenames.o readckt.o init_storage.o checkclock.o init_node.o genfault.o -lm

which is what I expected. Note that the -O4 option was present for compiling each .c file.

Now for the C++ codes, my makefile looks like this:

CC = g++
LDFLAGS = -lm
CFLAGS  = -O4

OBJS =     readckt.o \
    cmpLevel.o

readckt : $(OBJS) readckt.h
    ${CC} ${CFLAGS} -o $@ ${OBJS} ${LDFLAGS} 

which uses the same formula as the one for the C codes. The compilation message outputs are:

 g++    -c -o readckt.o readckt.cpp
g++    -c -o cmpLevel.o cmpLevel.cpp
g++ -O4 -o readckt readckt.o cmpLevel.o -lm

Note that while compiling the individual .cpp files, the -O4 option was not there.

My question is, what in the makefile that made it behave differently with C and C++ codes.

Please note that I am not very good in C/C++ programming and I only know the basic stuff. So excuse my rudimentary question and understanding on the subject. If you provide advices (for which I very much appreciate), please explain in simple terms.

Thank you.

---

### Post by MadCow108 on 2012-03-03
you are making use of implicit rules where compilation flags for c++ are named CPPFLAGS not CFLAGS
the detection of what it uses what is based on the file extensions.

[http://www.ecoop.net/coop/translated/GNUMake3.77/make_10.html](http://www.ecoop.net/coop/translated/GNUMake3.77/make_10.html)

---

### Post by chenxinghao on 2012-03-03
Go it!

Is it because CFLAGS is a reserved variable name?

I thought it was just any name for users to use.

Thank you.

---

### Post by MadCow108 on 2012-03-03
its not reserved its just a make convention to use CFLAGS for C and CPPFLAGS for C++, makes implicit rules make use of that.

If you write the rules explicitly you can use whatever variable names you like.

---

### Post by SevenMachines on 2012-03-04
CPPFLAGS are the preprocessor flags, generally passed to just about everything. The c++ version of CFLAGS confusingly are the CXXFLAGS. Unless sundays taken my brain I think thats right anyway

---

### Post by SevenMachines on 2012-03-04
I always remember man but forget info... anyway I thought it might be in there somewhere
```
$ info automake "Standard Configuration Variables"

```
> 2.2.4 Standard Configuration Variables
--------------------------------------

The GNU Coding Standards also define a set of standard configuration
variables used during the build.  Here are some:

`CC'
     C compiler command

`CFLAGS'
     C compiler flags

`CXX'
     C++ compiler command

`CXXFLAGS'
     C++ compiler flags

`LDFLAGS'
     linker flags

`CPPFLAGS'
     C/C++ preprocessor flags


---

