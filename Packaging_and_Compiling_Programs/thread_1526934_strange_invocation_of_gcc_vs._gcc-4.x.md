---
title: "strange invocation of gcc vs. gcc-4.x"
date: 2010-07-08
forum: Packaging and Compiling Programs
---

### Post by darrenleeweber on 2010-07-08
I'm getting some weird behavior when calling gcc on a basic hello world program.  When gcc is called without a version specific suffix, there is an '-iprefix' setting that screws up the include path.  When a version specific suffix is used, it works fine.

Here's what I get:

```

dweber@weberT61:~/tmp$ uname -a
Linux weberT61 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
dweber@weberT61:~/tmp$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"
dweber@weberT61:~/tmp$ cat tmp.c

#include <stddef.h>
#include <stdio.h>

int main(void)
{
  printf("Hello world!\n");
  return 0;
}

dweber@weberT61:~/tmp$ which gcc
/usr/bin/gcc
dweber@weberT61:~/tmp$ ls -l /usr/bin/gcc
lrwxrwxrwx 1 root root 21 2010-07-08 13:41 /usr/bin/gcc -> /etc/alternatives/gcc*
dweber@weberT61:~/tmp$ ls -l /etc/alternatives/gcc
lrwxrwxrwx 1 root root 16 2010-07-08 13:41 /etc/alternatives/gcc -> /usr/bin/gcc-4.3*
dweber@weberT61:~/tmp$ gcc -v tmp.c
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.4-10ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.4 (Ubuntu 4.3.4-10ubuntu1) 
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.3.4/cc1 -quiet -v -iprefix /home/dweber/bin/../lib/gcc/x86_64-linux-gnu/4.3.4/ tmp.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase tmp.c -mtune=generic -auxbase tmp -version -fstack-protector -o /tmp/ccBC3SQw.s
ignoring nonexistent directory "/home/dweber/bin/../lib/gcc/x86_64-linux-gnu/4.3.4/include"
ignoring nonexistent directory "/home/dweber/bin/../lib/gcc/x86_64-linux-gnu/4.3.4/include-fixed"
ignoring nonexistent directory "/home/dweber/bin/../lib/gcc/x86_64-linux-gnu/4.3.4/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/home/dweber/bin/../lib/gcc/../../lib/gcc/x86_64-linux-gnu/4.3.4/include"
ignoring nonexistent directory "/home/dweber/bin/../lib/gcc/../../lib/gcc/x86_64-linux-gnu/4.3.4/include-fixed"
ignoring nonexistent directory "/home/dweber/bin/../lib/gcc/../../lib/gcc/x86_64-linux-gnu/4.3.4/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/include
End of search list.
GNU C (Ubuntu 4.3.4-10ubuntu1) version 4.3.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.3.4, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a71ddfbbed0b03b3fcc5bfe2f38648db
tmp.c:2:20: error: stddef.h: No such file or directory
In file included from /usr/include/stdio.h:75,
                 from tmp.c:3:
/usr/include/libio.h:53:21: error: stdarg.h: No such file or directory
In file included from /usr/include/stdio.h:75,
                 from tmp.c:3:
/usr/include/libio.h:332: error: expected specifier-qualifier-list before ‘size_t’
/usr/include/libio.h:364: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:373: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/libio.h:491: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/libio.h:493: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/libio.h:495: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘_IO_sgetn’
In file included from tmp.c:3:
/usr/include/stdio.h:296: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:302: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:314: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:321: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:349: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:354: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:357: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:363: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:365: error: format string argument not a string type
/usr/include/stdio.h:367: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:368: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:369: error: format string argument not a string type
/usr/include/stdio.h:395: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:454: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:461: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:466: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:476: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:481: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:484: error: expected declaration specifiers or ‘...’ before ‘__gnuc_va_list’
/usr/include/stdio.h:639: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:642: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:652: error: expected declaration specifiers or ‘...’ before ‘size_t’
/usr/include/stdio.h:682: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread’
/usr/include/stdio.h:688: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite’
/usr/include/stdio.h:710: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fread_unlocked’
/usr/include/stdio.h:712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fwrite_unlocked’
dweber@weberT61:~/tmp$ gcc-4.3 -v tmp.c
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.4-10ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.4 (Ubuntu 4.3.4-10ubuntu1) 
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.3.4/cc1 -quiet -v tmp.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase tmp.c -mtune=generic -auxbase tmp -version -fstack-protector -o /tmp/ccpAkqNS.s
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.3.4/include
 /usr/lib/gcc/x86_64-linux-gnu/4.3.4/include-fixed
 /usr/include
End of search list.
GNU C (Ubuntu 4.3.4-10ubuntu1) version 4.3.4 (x86_64-linux-gnu)
	compiled by GNU C version 4.3.4, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: a71ddfbbed0b03b3fcc5bfe2f38648db
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 as -V -Qy -o /tmp/ccsqq73o.o /tmp/ccpAkqNS.s
GNU assembler version 2.20.1 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.20.1-system.20100303
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.3.4/:/usr/lib/gcc/x86_64-linux-gnu/4.3.4/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.3.4/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.3.4/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.3.4/:/usr/lib/gcc/x86_64-linux-gnu/4.3.4/:/usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../:/lib/:/usr/lib/:/usr/lib/x86_64-linux-gnu/
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.3.4/collect2 --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=both -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro /usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../../lib/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.3.4/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.3.4 -L/usr/lib/gcc/x86_64-linux-gnu/4.3.4 -L/usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../.. -L/usr/lib/x86_64-linux-gnu /tmp/ccsqq73o.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.3.4/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.3.4/../../../../lib/crtn.o
dweber@weberT61:~/tmp$ ./a.out 
Hello world!
dweber@weberT61:~/tmp$ gcc-4.4 -v tmp.c
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.4.3/cc1 -quiet -v tmp.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase tmp.c -mtune=generic -auxbase tmp -version -fstack-protector -o /tmp/ccwOKUvf.s
GNU C (Ubuntu 4.4.3-4ubuntu5) version 4.4.3 (x86_64-linux-gnu)
	compiled by GNU C version 4.4.3, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include-fixed
 /usr/include
End of search list.
GNU C (Ubuntu 4.4.3-4ubuntu5) version 4.4.3 (x86_64-linux-gnu)
	compiled by GNU C version 4.4.3, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 2129e1a56226bd6e8f7af5e0a3ff467d
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 as -V -Qy -o /tmp/ccmIRdHO.o /tmp/ccwOKUvf.s
GNU assembler version 2.20.1 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.20.1-system.20100303
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.4.3/:/usr/lib/gcc/x86_64-linux-gnu/4.4.3/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.3/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.3/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.4.3/:/usr/lib/gcc/x86_64-linux-gnu/4.4.3/:/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../:/lib/:/usr/lib/:/usr/lib/x86_64-linux-gnu/
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.4.3/collect2 --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=both -dynamic-linker /lib64/ld-linux-x86-64.so.2 -z relro /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.4.3/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.4.3 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.3 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../.. -L/usr/lib/x86_64-linux-gnu /tmp/ccmIRdHO.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/x86_64-linux-gnu/4.4.3/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.4.3/../../../../lib/crtn.o
dweber@weberT61:~/tmp$ ./a.out 
Hello world!
dweber@weberT61:~/tmp$ 

```

---

### Post by Tom Dignan on 2010-07-11
Why are you including stddef.h? You have no reason to include it.

---

