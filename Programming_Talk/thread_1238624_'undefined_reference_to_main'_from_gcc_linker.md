---
title: "'undefined reference to main' from gcc linker"
date: 2009-08-12
forum: Programming Talk
---

### Post by 1500 on 2009-08-12
I get this error trying to link hello.o using terminal.  I get this with hello.o compiled from either gcc or g++ each with the appropriate source.  

This gets worse.  I have an older system also with 9.04 which works fine on this.
I have reinstalled 9.04 from scratch on my main system.  'Build Essential' is installed.

The gcc -v output is slightly different on the 2 machines.
Next is a portion of the output from the failed machine.
COLLECT_GCC_OPTIONS='-v' '-mtune=generic'
 /usr/lib/gcc/i486-linux-gnu/4.3.3/collect2 --eh-frame-hdr -m elf_i386 --hash-style=both -dynamic-linker /lib/ld-linux.so.2 -z relro /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.3.3 -L/usr/lib/gcc/i486-linux-gnu/4.3.3 -L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../.. hello.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crtn.o

/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status

This output is from the system that worked.  The last line or so is different:
COLLECT_GCC_OPTIONS='-v' '-shared-libgcc' '-mtune=generic'
 /usr/lib/gcc/i486-linux-gnu/4.3.3/collect2 --eh-frame-hdr -m elf_i386 --hash-style=both -dynamic-linker /lib/ld-linux.so.2 -z relro /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.3.3/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.3.3 -L/usr/lib/gcc/i486-linux-gnu/4.3.3 -L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.3.3/../../.. hello.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/i486-linux-gnu/4.3.3/crtend.o /usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crtn.o

---

### Post by SledgeHammer_999 on 2009-08-12
can you show the code?

---

### Post by Can+~ on 2009-08-12
> **SledgeHammer_999 said:**
> can you show the code?

+1

Plus showing how are you trying to compile and link it.

---

### Post by 1500 on 2009-08-13
2 responses asked for the code.  First with C
#include <stdio.h>
/*   Using this to test my linking problem with gcc on 08Dell. */
int Main (void)
{
    printf ("Hello, world!\n");
    return 0;
}
gcc -Wall -c hello.c
gcc -v hello.o -o hello

2nd with c++.
#include <iostream>

int Main()
{
    std::cout << "Hello World!\n";
    return 0;
}
g++ -Wall -c hello.cpp
g++  -v hello.o -o hello

I have had this problem with other items.  These were done to try to simplify the case.
Again I ran the g++ case on an older machine also with 9.04.  It links fine there.

Thanks

---

### Post by MadCow108 on 2009-08-13
main needs to be lowercase
C is case sensitive

---

### Post by 1500 on 2009-08-13
This is embarrassing.  Needless to say the case that ran on the other machine was typed lower case.
I did a similar thing with 'main' about 25 years ago.  I'm just getting back to C now in retirement.

Thanks

---

