---
title: "Scary Intermittant 'aborted' error"
date: 2006-10-11
forum: Programming Talk
---

### Post by Relain on 2006-10-11
Hi, 
So i'm working on an N-Body simlation in C++, using the Barnes Hut tree algorithim for them that knows about these things. The code seems to work fairly well, when it actually works. The problem is that about 80% of the tim when i try to launch the file i get the error: Aborted and it doesn't go, occaisionally it seg-faults too. This is certainly not one of my own error checking things causing an exit(). Where does it come from? What does it mean? Can i use something to find out why it's dying? Will it be in a log somewhere?

Now i've tried it through gdb and it seems to work fine then (can't reproduce the problem), i tested it out with valgrind and it didn't find any memory leaks and so forth. As far as i could understand the output valgrind was mostly just pissed off with functions in standard libraries like Math::Pow. 

Also when it does actually start running it'll go for days, i ran it for ~ 200 hours no problem. 

It's compiled with the ICC and G++ and it happens with both afaik. The code uses OMP quite heavily but this can be turned off and it still works.

Uname -A gives: Linux Raskolnikov 2.6.15-27-amd64-generic #1 SMP PREEMPT Sat Sep 16 01:50:50 UTC 2006 x86_64 GNU/Linux

Icc -v gives: Version 9.1
g++ -v gives: Configured with: ../src/configure -v --enable-languages=c,c++,java,f95,objc,ada,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.0 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-java-awt=gtk-default --enable-gtk-cairo --with-java-home=/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre --enable-mpfr --disable-werror --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

I wonder if anyone else knows what the problem might be? I'm not mallocing anything! 

Also i can tarball the code if anyone wants it...

---

### Post by jmillikin on 2006-10-12
Welcome to the world of debugging. First, compile with full debug flags and no optimizations - CPPFLAGS should contain -g3 -O0.

I'd run the program in Valgrind in single-threaded mode. Every time it outputs an error, trace the error back into your code. The standard library does not typically cause Valgrind errors (except X11, ick). If Valgrind says that pow() is accessing bad memory, it means your program passed it bad memory. If you can't see where your program is going wrong, post the log here and we can help.

If you've got a clean Valgrind output, and the program still happens, you'll have to use GDB. It's not very hard - run your program as "gdb ./myprogramhere", type "run", and then wait for something bad to happen. When it crashes, type "bt" and either read it yourself, or post it here to get some help.

Good luck. Debugging memory-related crashes is why interpreted languages are so popular.

---

### Post by amo-ej1 on 2006-10-12
what i'd do in such cases. First I'd make sure i'd be able to get to some core dumps -> ```
ulimit -c 99999999 
``` (this only works in your current shell by adapting the user limits) When your program segfaults it will leave a core dump behind (in the current working directory). You can open this in gdb and at that point you can try to find the origin of your error.

---

### Post by Relain on 2006-10-12
The core dumps thing sounds like a good idea, i'll try that. I've already pushed it through gdb but it didn't fail. Also how do you make gdb evaluate more then line by line. I thought it was: Next or Until but it seems to just go one bit at a time, which when you have >2k lines of code and huge loops is a little useless.

As for interpreted languages, they're too slow for the amount of particles i need to be simulating. I fear i really should have done this in straight C but pointers get tiresome. 

I'll post any further resutls. Thanks guys!

---

### Post by Relain on 2006-10-13
Hey again, thanks for the suggestions. I've managed to try some things iout and it's a little baffling. 

I'm a (trainee) scientist, not a comp genius and i sadly have no idea what these mean:

Valgrind output: compiled with -O0 -g3
```

==28088== Memcheck, a memory error detector.
==28088== Copyright (C) 2002-2005, and GNU GPL'd, by Julian Seward et al.
==28088== Using LibVEX rev 1471, a library for dynamic binary translation.
==28088== Copyright (C) 2004-2005, and GNU GPL'd, by OpenWorks LLP.
==28088== Using valgrind-3.1.0-Debian, a dynamic binary instrumentation framework.
==28088== Copyright (C) 2000-2005, and GNU GPL'd, by Julian Seward et al.
==28088== For more details, rerun with: -v
==28088==
KE = 1.31081 PE = 2.14683
killed one!
31467.4 1121.53 30345.9
==28088== Stack overflow in thread 1: can't grow stack to 0x7FE801FD8
==28088==
==28088== Process terminating with default action of signal 11 (SIGSEGV): dumping core
==28088==  Access not within mapped region at address 0x7FE801FD8
==28088==    at 0x40AAE6: ntree_iterator<quad_node, quad_node&, quad_node*>::check_non_null() const (ntree.tpp:265)
==28088== Stack overflow in thread 1: can't grow stack to 0x7FE801FD0
==28088==
==28088== Process terminating with default action of signal 11 (SIGSEGV)
==28088==  Access not within mapped region at address 0x7FE801FD0
==28088==    at 0x491763A: _vgw_freeres (vg_preloaded.c:58)
==28088==
==28088== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 10 from 1)
==28088== malloc/free: in use at exit: 3,928,472 bytes in 20,669 blocks.
==28088== malloc/free: 57,400 allocs, 36,731 frees, 9,022,504 bytes allocated.
==28088== For counts of detected errors, rerun with: -v
==28088== searching for pointers to 20,669 not-freed blocks.
==28088== checked 5,324,968 bytes.
==28088==
==28088== LEAK SUMMARY:
==28088==    definitely lost: 0 bytes in 0 blocks.
==28088==      possibly lost: 0 bytes in 0 blocks.
==28088==    still reachable: 3,928,472 bytes in 20,669 blocks.
==28088==         suppressed: 0 bytes in 0 blocks.
==28088== Reachable blocks (those to which a pointer was found) are not shown.
==28088== To see them, rerun with: --show-reachable=yes

```

and gdb is equally cryptic:

```

[Raskolnikov:src]:gdb ./Nbody_ICC.out core
GNU gdb 6.4-debian
Copyright 2005 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...Using host libthread_db library "/lib/libthread_db.so.1".

Core was generated by `./Nbody_ICC.out'.
Program terminated with signal 11, Segmentation fault.
Reading symbols from /usr/lib/libgsl.so.0...done.
Loaded symbols for /usr/lib/libgsl.so.0
Reading symbols from /usr/lib/libgslcblas.so.0...done.
Loaded symbols for /usr/lib/libgslcblas.so.0
Reading symbols from /lib/libm.so.6...done.
Loaded symbols for /lib/libm.so.6
Reading symbols from /usr/lib/libstdc++.so.6...done.
Loaded symbols for /usr/lib/libstdc++.so.6
Reading symbols from /lib/libgcc_s.so.1...done.
Loaded symbols for /lib/libgcc_s.so.1
Reading symbols from /opt/intel/cce/9.1.043/lib/libcxaguard.so.5...done.
Loaded symbols for /opt/intel/cce/9.1.043/lib/libcxaguard.so.5
Reading symbols from /lib/libc.so.6...done.
Loaded symbols for /lib/libc.so.6
Reading symbols from /lib/libdl.so.2...done.
Loaded symbols for /lib/libdl.so.2
Reading symbols from /lib/ld-linux-x86-64.so.2...done.
Loaded symbols for /lib64/ld-linux-x86-64.so.2
Dwarf Error: Cannot find DIE at 0x2faef referenced from DIE at 0x2fb25 [in module /home/chris/Projects/NbodyE/trunk/src/Nbody_ICC.out]
Dwarf Error: Cannot find DIE at 0x2faef referenced from DIE at 0x2fb25 [in module /home/chris/Projects/NbodyE/trunk/src/Nbody_ICC.out]
(gdb) backtrace
Dwarf Error: Cannot find DIE at 0x2faef referenced from DIE at 0x2fb25 [in module /home/chris/Projects/NbodyE/trunk/src/Nbody_ICC.out]
Dwarf Error: Cannot find DIE at 0x2faef referenced from DIE at 0x2fb25 [in module /home/chris/Projects/NbodyE/trunk/src/Nbody_ICC.out]
(gdb)

```

What the hell is Dwarf? I have no idea what DIE is either? There's no calls to DIE in my code as far as i know. What does a stack overflow mean? I'm not mallocing things, there's some new / delete action but i thought C++ was able to handle that. The crashing seems to be related to the number of particles i try and simulate them and the corseness of the time-stepping, i don't really understand how this would break things.

Any ideas? Thanks. :confused:

---

### Post by maubp on 2006-10-16
You could try runnung valgrind with the --show-reachable=yes option, that might help.  It has other more details options.

I've got no idea what the Dwarf Error: Cannot find DIE is about.  A little googling suggests its some debugging format.

One other thing you could do is install debugging versions of any special libraries you use (might give meaningful variables names for example).

---

### Post by public_void on 2006-10-16
From the output I think its a segmentation fault, suggesting the program is accessing a memory location it shouldn't be. I'm not certain as I'm not too familiar with gdb. 

> ==28088== Stack overflow in thread 1: can't grow stack to 0x7FE801FD8
==28088==
==28088== **Process terminating with default action of signal 11** (SIGSEGV): dumping core
==28088==  Access not within mapped region at address 0x7FE801FD8

> Core was generated by `./Nbody_ICC.out'.
Program terminated with **signal 11, Segmentation fault.**
Reading symbols from /usr/lib/libgsl.so.0...done.

---

### Post by red_Marvin on 2006-10-16
Just stating the obvious, do you check that each allocated pointer is valid (allocation/new succeeded)?

In my (small) experience segfaults often come from bad pointers...

---

