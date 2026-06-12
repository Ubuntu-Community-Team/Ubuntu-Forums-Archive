---
title: "GCC paths WRONG but CodeBlocks Compiles OK??"
date: 2013-04-25
forum: Packaging and Compiling Programs
---

### Post by jerecb on 2013-04-25
OK, so I'm cross-compiling PowerPC code in Ubuntu on an x86 machine. 

GCC for x86 is working fine. I installed a PowerPC GCC package but it made code which wouldn't work on my target platform. However, someone sent me an older GCC-PowerPC compiler. It came as a .gz which I simply extracted into /usr. 

So here's where things get messy. I've been using CodeBlocks to write C code. I pointed it's "compiler executable" to the new compiler, and hey presto, PowerPC executable compiled fine and worked. 

But I don't know how. 

The problem is I can't get it to work from a makefile or the command line. I get messages saying it can't find the (standard) include files, and if I add include file paths into the compiler options I get an error message for nearly every line in every include file - e.g. 

```

In file included from main.c:2:/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:583: error: parse error before "__size"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:739: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:743: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:812: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:815: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:819: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:822: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:830: error: parse error before "size_t"
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:833: error: parse error before '*' token
/usr/powerpc-linux/gcc-3.4.3-glibc-2.3.3/powerpc-linux/include/stdlib.h:837: error: parse error before "wchar_t"
....etc

```

If I try the -print-search-dirs option for this GCC version, I get loads of paths with some which are wrong (probably from the machine the compiler was originally installed on). 

Even stranger, if I copy the exact command line compiler call from Code::Blocks, like this: 

```

powerpc-linux-gcc -Wall  -O2  -Wmain    -c /home/jeremy/cprojects/HelloWorld/HelloWorld.c -o /home/jeremy/cprojects/HelloWorld/HelloWorld.o

```

I get 

```

powerpc-linux-gcc: HelloWorld.c: No such file or directory
powerpc-linux-gcc: no input files

```

I tried giving the full path for HelloWorld.c but it was exactly the same!! (yes HelloWorld.c is there...)

So I know the compiler isn't installed properly, but HOW does CodeBlocks manage to compile? Why can't I do whatever it does, from the command line or a makefile?? All I've done is told it the base path where the compiler executables are, and the executable to run for GCC. No other paths or libraries are mentioned. This is driving me nuts!

Also, is it possible to change the default paths that a GCC install uses (as returned by -print-search-dirs)? Are they in a config file somewhere?

I'd like to install it properly, of course, but it's some special build for the hardware and I wasn't given an install package. I don't know if that's an option.

---

