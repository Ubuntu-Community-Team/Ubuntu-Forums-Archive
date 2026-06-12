---
title: "Unable to see debug symbols inspite using -g flag"
date: 2013-07-12
forum: Programming Talk
---

### Post by Blackbug on 2013-07-12
Hi

I am using Red Hat Linux at work. I am trying to debug an application in development enviornment, but unable to see the debug information in GDB.
I have double checked the makefiles, and "-g" flag is being used while compilation.
I even tried other flag -gdwarf & -gstabs but no use.

I set couple of breakpoints on initializing methods which are hit when I run the application, but the program quits silently without hitting the breakpoints.

I am seeing something like below:

[New Thread 46912753450944 (LWP 14004)]
[Switching to Thread 46912753450944 (LWP 14004)]
0x0000000000405488 in main ()
(gdb) where
#0  0x0000000000405488 in main ()
(gdb) bt
#0  0x0000000000405488 in main ()
(gdb) n
Single stepping until exit from function main,
which has no line number information.
0x0000003770c1d8a4 in __libc_start_main () from /lib64/libc.so.6
(gdb) stepi
0x0000003770c1d8a6 in __libc_start_main () from /lib64/libc.so.6
(gdb) stepi
0x0000003770c32c50 in exit () from /lib64/libc.so.6
(gdb) n
Single stepping until exit from function exit,
which has no line number information.
 
Program exited with code 01.

Any suggestions?

---

### Post by trent.josephsen on 2013-07-12
Just a guess -- was it recently that you added -g to CFLAGS? Editing a Makefile doesn't cause targets to be rebuilt. If you need everything to be rebuilt with the new settings, use make -B.

---

### Post by Blackbug on 2013-07-12
> **trent.josephsen said:**
> Just a guess -- was it recently that you added -g to CFLAGS? Editing a Makefile doesn't cause targets to be rebuilt. If you need everything to be rebuilt with the new settings, use make -B.

I did a clean build, so everything is build from scratch, so I think debug symbols are present in the required libs and binaries.

---

### Post by james_mcl on 2013-08-09
Have you tried compiling with -g -gdwarf-2 to get the DWARF debugging symbols in an older format which may not have compatibility issues with gdb?

> 
[http://gcc.gnu.org/gcc-4.8/changes.html](http://gcc.gnu.org/gcc-4.8/changes.html)

...

DWARF4 is now the default when generating DWARF debug information. When -g is used on a platform
that uses DWARF debugging information, GCC will now default to -gdwarf-4 -fno-debug-types-section.

GDB 7.5, Valgrind 3.8.0 and elfutils 0.154 debug information consumers support DWARF4 by default.
Before GCC 4.8 the default version used was DWARF2. To make GCC 4.8 generate an older DWARF version
use -g together with -gdwarf-2 or -gdwarf-3. The default for Darwin and VxWorks is still -gdwarf-2 -gstrict-dwarf.


---

### Post by dwhitney67 on 2013-08-09
> **Blackbug said:**
> 
Any suggestions?

Why not just show us how you are building the application; that is, show us the Makefile.  Are you using C (CFLAGS) or C++ (CXXFLAGS) to define the -g?

I find it doubtful that if you set the -g option, and saw it during the compilation phase of your application, that it would not produce symbolic information.

---

