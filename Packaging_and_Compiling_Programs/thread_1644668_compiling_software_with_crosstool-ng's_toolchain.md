---
title: "compiling software with crosstool-ng's toolchain"
date: 2010-12-13
forum: Packaging and Compiling Programs
---

### Post by terminator14 on 2010-12-13
I'm trying to compile some software for an embedded linux system using crosstool-ng and I seem to be stuck. I have created a toolchain using crosstool-ng on another box, but now that box has 2 compilers - the gcc compiler it had installed and the newly created one that's part of a toolchain. The entire toolchain was installed to a folder at ~/x-tools. I know I can compile programs one file at a time with the newly created gcc compiler (toolchain_gcc -o test_prog test.c), but what if I want to compile an entire program from source?

If I have a program, lets say a calculator that I downloaded as calc.tar.gz:

I untar it
cd into folder

then what? How do I tell ./configure and 'make' that I want to use the toolchain to compile the program and not the OS's regular compiler?

---

### Post by File_ on 2010-12-15
> **terminator14 said:**
> 
then what? How do I tell ./configure and 'make' that I want to use the toolchain to compile the program and not the OS's regular compiler?

Make is using Makefile to compile program. In header of Makefile there is usually CC flag which is telling make what compiler to use. Try changing that to your own compiler like 
```
CC=toolchain_gcc
```Try reading some Makefile tutorials: [http://mrbook.org/tutorials/make/](http://mrbook.org/tutorials/make/)
Here are explained configure, make and make install: [http://tldp.org/LDP/LG/current/smith.html](http://tldp.org/LDP/LG/current/smith.html)

---

### Post by SevenMachines on 2010-12-15
Dont know about how crosstool-ng does things, but ./configure uses the --host option when cross compiling, although i'm no expert on cross compiling.
Heres an example using the arm gcc cross compiling libraries from the repository  and the 'hello' source package
> 
$ sudo apt-get install gcc-arm-linux-gnueabi 
$ apt-get source hello
$ cd hello-2.5/
$ ./configure --host arm-linux-gnueabi
 $ make
$ file src/hello

src/hello: ELF 32-bit LSB executable, ARM, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.16, not stripped

---

### Post by terminator14 on 2010-12-16
> **SevenMachines said:**
> Dont know about how crosstool-ng does things, but ./configure uses the --host option when cross compiling, although i'm no expert on cross compiling.
Heres an example using the arm gcc cross compiling libraries from the repository  and the 'hello' source package

I read somewhere about that. This should be useful if I am compiling something from an x64 system onto an x86 system, or the other way around - which I do sometimes. Thanks. The problem with using this to compile something for an embedded system seems to be the fact that even though the architecture for which you are building changes here, the versions of glibc and other libraries stay the same. That means if the embedded system is using an older glibc library and I compile software on a different machine with a newer glibc library, the application will complain as soon as it is transfered over and run on the embedded system despite being the correct architecture. This is to the best of my understanding of course - I could be wrong here, but I'm pretty sure I've seen this happen (unless the errors about the glibc version mismatches I read were about some other problem).

> **File_ said:**
> Make is using Makefile to compile program. In header of Makefile there is usually CC flag which is telling make what compiler to use. Try changing that to your own compiler like 
```
CC=toolchain_gcc
```Try reading some Makefile tutorials: [http://mrbook.org/tutorials/make/](http://mrbook.org/tutorials/make/)
Here are explained configure, make and make install: [http://tldp.org/LDP/LG/current/smith.html](http://tldp.org/LDP/LG/current/smith.html)

I think this is the solution I was trying, although I was trying it through an argument to ./configure like I've seen used in a few samples of code around the net, rather the modifying the Makefile. I'm pretty sure the result should have been the same. I kept getting errors while trying to compile the test program, but now that I look at it, it seems the test program was written in cpp, while, during the configuration stages of the toolchain I was making, I left cpp out of the gcc that was compiled (which was the default). That may have been the problem that I misinterpreted for the argument I was using not working. I'm going to try to recompile the toolchain with cpp enabled this time, and try either the argument of CC= that I kept passing to the configure script, or I'll try your suggestion and modify the Makefile to change the CC variable. Thanks.

Oh and if the compiler is supposed to be a C++ compiler rather than a C compiler, does anything change? Doesn't CC stand for C Compiler? Does that mean there is another variable I have to change for C++, or is this variable still the one that needs to be modified? And am I still pointing it to the gcc file, or is there some other file it needs to point to (like g++ or something?). There were several files created in the toolchain - linkers and loaders and all kinds of stuff I don't fully understand - are any of them the C++ compiler or is it still gcc?

And if the compiler needs to use the glibc library, how can I tell it to use the glibc library that's part of the toolchain, and not the library installed on the OS I'm compiling (in /lib)? Or does the toolchain's gcc somehow know to do that automatically?

---

### Post by terminator14 on 2010-12-16
Having recreated the toolchain with C++ enabled, it appears in order to compile a program using the toolchain, I need to run the program's configure script with the following:

./configure CC=~/x-tools/i686-nptl-linux-gnu/bin/i686-nptl-linux-gnu-gcc --host=x86_64-unknown-linux-gnu CXX=~/x-tools/i686-nptl-linux-gnu/bin/i686-nptl-linux-gnu-g++

the CC points to the C Compiler while the CXX appears to point to the C++ compiler - g++. --host is determined by config.guess that comes with the source of many programs. After running the line above, the CC and CXX variables within the Makefile change to reflect the gcc and g++ files above. Compiling the program with these settings was nearly successful. I did get some errors during compilation that I'm trying to fix but they seem to be unrelated.

Thanks for your help guys.

---

