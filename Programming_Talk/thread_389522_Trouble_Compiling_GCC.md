---
title: "Trouble Compiling GCC"
date: 2007-03-20
forum: Programming Talk
---

### Post by steve_loudon on 2007-03-20
I am trying to recreate the binaries for a arm cross compiler (gcc-3.2.3) that I have on another machine.  I am currently running Ubuntu 6.10 with the latest stable version of gcc installed (gcc-4.1.2).

I have not built gcc before, so I thought that the easiest thing to do first is to just recompile version 4.1.2.  I got the source, ran configure and make.  It ended in error.

I used the following configure options:

 ../src/gcc-4.1.2/configure --prefix=/home/loudon --disable-werror --enable-languages=c

and the make bootstrap command ended with the following error:


/home/loudon/gcc-build/./gcc/xgcc -B/home/loudon/gcc-build/./gcc/ -B/home/loudon/i686-pc-linux-gnu/bin/ -B/home/loudon/i686-pc-linux-gnu/lib/ -isystem /home/loudon/i686-pc-linux-gnu/include -isystem /home/loudon/i686-pc-linux-gnu/sys-include -O2  -O2 -g -O2   -DIN_GCC    -W -Wall -Wwrite-strings -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include  -fPIC -g -DHAVE_GTHR_DEFAULT -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED  -I. -I. -I../../src/gcc-4.1.2/gcc -I../../src/gcc-4.1.2/gcc/. -I../../src/gcc-4.1.2/gcc/../include -I../../src/gcc-4.1.2/gcc/../libcpp/include  -fexceptions -fvisibility=hidden -DHIDE_EXPORTS -c ../../src/gcc-4.1.2/gcc/unwind-dw2.c -o libgcc/./unwind-dw2.o
In file included from ../../src/gcc-4.1.2/gcc/unwind-dw2.c:256:
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h: In function ‘x86_fallback_frame_state’:
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:152: error: ‘struct sigcontext’ has no member named ‘esp’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:159: error: ‘struct sigcontext’ has no member named ‘eax’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:161: error: ‘struct sigcontext’ has no member named ‘ebx’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:163: error: ‘struct sigcontext’ has no member named ‘ecx’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:165: error: ‘struct sigcontext’ has no member named ‘edx’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:167: error: ‘struct sigcontext’ has no member named ‘esi’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:169: error: ‘struct sigcontext’ has no member named ‘edi’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:171: error: ‘struct sigcontext’ has no member named ‘ebp’
../../src/gcc-4.1.2/gcc/config/i386/linux-unwind.h:173: error: ‘struct sigcontext’ has no member named ‘eip’
make[4]: *** [libgcc/./unwind-dw2.o] Error 1
make[4]: Leaving directory `/home/loudon/gcc-build/gcc'
make[3]: *** [libgcc.a] Error 2
make[3]: Leaving directory `/home/loudon/gcc-build/gcc'
make[2]: *** [all-stage1-gcc] Error 2
make[2]: Leaving directory `/home/loudon/gcc-build'
make[1]: *** [stage1-bubble] Error 2
make[1]: Leaving directory `/home/loudon/gcc-build'
make: *** [all] Error 2


Don't know where to go from here.  When I looked through the .h files that should have defined sigcontext, the structure members should be defined.

Thanks for any suggestions,
Steve

---

