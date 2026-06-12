---
title: "Implementing"
date: 2005-10-08
forum: Programming Talk
---

### Post by Comrade on 2005-10-08
>  **  Python scripting everywhere**

   Python is a great glue language. Ubuntu is open to requests for funding work that needs to be done to make Python the most widespread common scripting language on the net. Please contact us with your ideas and proposals. 
      Bounties will be offered on Python scripting interfaces for the following tools:
   [LIST]
[*]OpenOffice
[*]Blender
[*]AbiWord
[*]Gnumeric
[*]The GIMP [/LIST]   We'd like to see the development of common document object model standards and terminology across OpenOffice, Abiword, Gnumeric, Agnubis, Sodipodi and other Gnome applications. This would accelerate the learning curve of someone who has already learned to script one app in Python, when they try to learn to script another. If anybody out there is good at drafting such specifications and is interested, please get in touch.
I'm not so interested in this particular bounty, but I am very interested in adding Python scriptability to applications. I am proficient in both Python and C++, but I have absolutely no idea on going about this task. I want to learn how to create Python scriptability in C++ applications like the ones listed above.

 
I realize how generic this is, but I need a direction to go.

---

### Post by toojays on 2005-10-08
Check out the chaper [Embedding Python in Another Application]("http://www.python.org/doc/2.4.2/ext/embedding.html") from the Python docs. I've never done this myself, but it is something which interests me as well.

Please post back and let us know how this goes.

---

### Post by Comrade on 2005-10-08
This is going to sound extremely noobish, but I am recieving these errors upon executing Jam.

> Jamfile  main.cpp
saketh@ubuntu:~/pyembed$ jam
...found 11 target(s)...
...updating 2 target(s)...
C++ main.o
main.cpp:1:20: Python.h: No such file or directory
main.cpp: In function `int main(int, char**)':
main.cpp:5: error: `Py_Initialize' undeclared (first use this function)
main.cpp:5: error: (Each undeclared identifier is reported only once for each
   function it appears in.)
main.cpp:7: error: `PyRun_SimpleString' undeclared (first use this function)main.cpp:8: error: `Py_Finalize' undeclared (first use this function)

cc -c -o main.o -O   main.cpp

...failed C++ main.o ...
...skipped pyembed for lack of main.o...
...failed updating 1 target(s)...
...skipped 1 target(s)...
I know what the error means, I probably haven't added Python.h to the compiler's list of include directories. However, I do not know how to do this on Linux (I am used to developing on Windows - I'm a spoiled brat). If someone could quickly clarify how to resolve this issue I would be grateful.

---

### Post by Comrade on 2005-10-08
I have resolved the headers issue (silly me - I forgot to add python2.4-dev in Synaptic!) and I need to include <python2.4/Python.h> instead of just <Python.h>.

But I still receive the following error, and I'd assume it's because I'm not linking to a certain library file.

> saketh@ubuntu:~/pyembed$ jam
...found 140 target(s)...
...updating 2 target(s)...
C++ main.o
Link pyembed
main.o(.text+0xa): In function `main':
: undefined reference to `Py_Initialize'
main.o(.text+0x16): In function `main':
: undefined reference to `PyRun_SimpleString'
main.o(.text+0x1b): In function `main':
: undefined reference to `Py_Finalize'
main.o(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

cc  -o pyembed  main.o

...failed Link pyembed ...
...failed updating 1 target(s)...
...updated 1 target(s)...
saketh@ubuntu:~/pyembed$

---

### Post by toojays on 2005-10-09
I'm not familiar with the output of jam, but from the looks of it, it's using the command line "cc -o pyembed main.o" to compile.

You are correct that you need to add the python library to the compiler command line. You can do this with a switch like "-lpython2.4" (use the python version number which is appropriate for your system, the python library is at /usr/lib/libpython*).

Also, for c++ code, you should be using c++ (or g++, it's the same thing) as the compiler, rather than cc. That will get rid of the last error you are getting, about gxx personality.

---

### Post by Comrade on 2005-10-09
Linux is so confusing - I can't even get this makefile stuff to work! There are no tutorials about get libraries to work with Jam, so I am stumped. 

Here is my makefile:
> pyembed: main.o
    g++ main.o

main.o: main.cpp
    g++ main.cpp -lpython2.4 -o main.o

When I type make, I get these errors:
> g++ main.o
collect2: ld terminated with signal 11 [Segmentation fault]
main.o(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.rodata+0x0):../sysdeps/i386/elf/start.S:47: first defined here
main.o(.data+0x4): In function `__data_start':
: multiple definition of `__dso_handle'
/usr/lib/gcc-lib/i486-linux/3.3.5/crtbegin.o(.data+0x0): first defined here
main.o(.init+0x0): In function `_init':
/home/drow/debian-glibc/glibc-2.3.2.ds1/build-tree/i386-libc/csu/crti.S:35: multiple definition of `_init'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crti.o(.init+0x0):/home/drow/debian-glibc/glibc-2.3.2.ds1/build-tree/i386-libc/csu/crti.S:12: first defined here
main.o(.text+0x0): In function `_start':
../sysdeps/i386/elf/start.S:47: multiple definition of `_start'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.text+0x0):../sysdeps/i386/elf/start.S:47: first defined here
main.o(.fini+0x0): In function `_fini':
/home/drow/debian-glibc/glibc-2.3.2.ds1/build-tree/i386-libc/csu/crti.S:51: multiple definition of `_fini'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crti.o(.fini+0x0): first defined heremain.o(*ABS*+0x80498b8): In function `__init_array_start':
main.cpp: multiple definition of `_GLOBAL_OFFSET_TABLE_'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.got.plt+0x0):../sysdeps/i386/elf/start.S:47: first defined here
main.o(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.rodata+0x4):../sysdeps/i386/elf/start.S:53: first defined here
main.o(.data+0x0): In function `__data_start':
: multiple definition of `__data_start'
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.data+0x0):../sysdeps/i386/elf/start.S:47: first defined here
/usr/lib/gcc-lib/i486-linux/3.3.5/../../../crt1.o(.dynamic+0x0):../sysdeps/i386/elf/start.S:47: multiple definition of `_DYNAMIC'
make: *** [pyembed] Error 1

This is pretty discouraging.

---

### Post by Comrade on 2005-10-09
Actually, I got it hacked together using a shell script. However, I do not think this is the best way to go. If someone could help me make this into a makefile that would be useful. 

compile.sh: g++ main.cpp -lpython2.4 -o pyembed

Then I do ./compile and it compiles. However, this just doesn't feel right.

---

### Post by toojays on 2005-10-09
The simplest Makefile to do what you want looks like this:```

# Use G++ to link main.o and libpython2.4 to make pyembed
pyembed: main.o
\tg++ -o pyembed -lpython2.4 main.o

# Use G++ to compile main.cpp into main.o
main.o : main.cpp
\tg++ -o main.o -c main.cpp
```(**Note:** I have used 
'\t' to indicate where a TAB character should be.)

The problem with your Makefile is that your rule to make main.o was compiling and linking in one step, and then trying to link a second time in your pyembed rule, resulting in redefinition errors. Your version of main.o was actually a working executable! What a difference one little switch (-c) can make!

P.S. You can actually take the above makefile and leave out the rule for make.o altogether, because GNU Make already knows how to make main.o from main.cpp.

---

### Post by Comrade on 2005-10-09
I am looking at [this tutorial.]("http://www.codeproject.com/useritems/embedpython_1.asp")

It seems to be more practical than the one over at python.org.

---

