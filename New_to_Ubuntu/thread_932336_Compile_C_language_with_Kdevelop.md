---
title: "Compile C language with Kdevelop"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by luckymancvp on 2008-09-28
In Kdevelop (c/c++), I choose new project : C, simple hello world program.
I creat a file : main.c  .After that I run : auto make and friends then press F8.
It appears:
```
cd '/home/luckymancvp/Example' && LDFLAGS="-T lnkscript crt0.o" CXX=arm-agb-elf-g++ CFLAGS="-nostartfiles" CC=arm-agb-elf-gcc "/home/luckymancvp/Example/configure" --host=arm-gcc-elf --build=i386
installing -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for arm-gcc-elf-strip... no
checking for strip... strip
checking for arm-gcc-elf-gcc... arm-agb-elf-gcc
configure: WARNING: In the future, Autoconf will not detect cross-tools
whose name does not start with the host triplet. If you think this
configuration is useful to you, please write to autoconf@gnu.org.
configure: error: C compiler cannot create executables
See `config.log' for more details.
checking for C compiler default output file name... 
*** Exited with status: 77 ***

```
I installed gcc.
So, how to solve this problem ?

---

### Post by TheLions on 2008-09-28
go to Build and press "Eun automake & friends", then build...

---

### Post by spec-chum on 2008-09-28
It sounds like you haven't installed the build-essential package.  You need this to be able to compile C programs.

Either use Synaptic to find it or run
```

sudo apt-get install build-essential

```

in the terminal

---

### Post by luckymancvp on 2008-09-28
Before that I usually compile with gcc, so I installed build-essential.

How to compile with Kdvelop.

---

