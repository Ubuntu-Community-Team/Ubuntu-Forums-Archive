---
title: "gcc provides no output file"
date: 2011-05-13
forum: Packaging and Compiling Programs
---

### Post by DMacATTACK on 2011-05-13
Hey all,

A while ago I tried installing libjpeg, and eventually switched computers. But after it I found that my gcc no longer worked. With a simple program such as this:

```
#include <stdio.h>

main()
{
printf("Hello World\n");
}
```


and compiling like this:
```

>> gcc test.c -o run
```

no output file is generated in the folder. (Normally you can run the file using ./run, but it is not in the folder). 

gcc IS working though, because if I have an error in the code such as

```
...
printZX("Hello World\n");
...
```

gcc complains and knows that it is not correct syntax... 

Any Ideas? This is really bugging me.```

```

---

### Post by MadCow108 on 2011-05-13
what does *gcc test.c -o run -v* output?

---

### Post by DMacATTACK on 2011-05-14
It outputs this:

```
$ gcc test.c -o run -v output 
gcc: output: No such file or directory
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
COLLECT_GCC_OPTIONS='-o' 'run' '-v' '-mtune=generic' '-march=i486'
 /usr/lib/gcc/i486-linux-gnu/4.4.3/cc1 -quiet -v test.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase test.c -mtune=generic -march=i486 -auxbase test -version -fstack-protector -o /tmp/ccnvsNdu.s
GNU C (Ubuntu 4.4.3-4ubuntu5) version 4.4.3 (i486-linux-gnu)
	compiled by GNU C version 4.4.3, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.4.3/include
 /usr/lib/gcc/i486-linux-gnu/4.4.3/include-fixed
 /usr/include
End of search list.
GNU C (Ubuntu 4.4.3-4ubuntu5) version 4.4.3 (i486-linux-gnu)
	compiled by GNU C version 4.4.3, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 5998ce5f1765e99eea5269f4c1e38d44
COLLECT_GCC_OPTIONS='-o' 'run' '-v' '-mtune=generic' '-march=i486'
 as -V -Qy -o /tmp/ccowln2j.o /tmp/ccnvsNdu.s
GNU assembler version 2.20.1 (i486-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.20.1-system.20100303
```

---

### Post by ApOgEEs on 2011-05-27
Before anything else, please check that you have write permission on that directory (folder) you are working on.

You may spot the differences between your output and my output.
```

apogee@apogee-ubox:~/Code/testc$ gcc test.c -o run -v 
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
COLLECT_GCC_OPTIONS='-o' 'run' '-v' '-mtune=generic' '-march=i486'
 /usr/lib/gcc/i486-linux-gnu/4.4.3/cc1 -quiet -v test.c -D_FORTIFY_SOURCE=2 -quiet -dumpbase test.c -mtune=generic -march=i486 -auxbase test -version -fstack-protector -o /tmp/ccWgBHjm.s
GNU C (Ubuntu 4.4.3-4ubuntu5) version 4.4.3 (i486-linux-gnu)
	compiled by GNU C version 4.4.3, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/i486-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../i486-linux-gnu/include"
ignoring nonexistent directory "/usr/include/i486-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/local/include
 /usr/lib/gcc/i486-linux-gnu/4.4.3/include
 /usr/lib/gcc/i486-linux-gnu/4.4.3/include-fixed
 /usr/include
End of search list.
GNU C (Ubuntu 4.4.3-4ubuntu5) version 4.4.3 (i486-linux-gnu)
	compiled by GNU C version 4.4.3, GMP version 4.3.2, MPFR version 2.4.2-p1.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 5998ce5f1765e99eea5269f4c1e38d44
COLLECT_GCC_OPTIONS='-o' 'run' '-v' '-mtune=generic' '-march=i486'
 as -V -Qy -o /tmp/ccuXcZyI.o /tmp/ccWgBHjm.s
GNU assembler version 2.20.1 (i486-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.20.1-system.20100303
COMPILER_PATH=/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../:/lib/:/usr/lib/:/usr/lib/i486-linux-gnu/
COLLECT_GCC_OPTIONS='-o' 'run' '-v' '-mtune=generic' '-march=i486'
 /usr/lib/gcc/i486-linux-gnu/4.4.3/collect2 --build-id --eh-frame-hdr -m elf_i386 --hash-style=both -dynamic-linker /lib/ld-linux.so.2 -o run -z relro /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crt1.o /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crti.o /usr/lib/gcc/i486-linux-gnu/4.4.3/crtbegin.o -L/usr/lib/gcc/i486-linux-gnu/4.4.3 -L/usr/lib/gcc/i486-linux-gnu/4.4.3 -L/usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/i486-linux-gnu/4.4.3/../../.. -L/usr/lib/i486-linux-gnu /tmp/ccuXcZyI.o -lgcc --as-needed -lgcc_s --no-as-needed -lc -lgcc --as-needed -lgcc_s --no-as-needed /usr/lib/gcc/i486-linux-gnu/4.4.3/crtend.o /usr/lib/gcc/i486-linux-gnu/4.4.3/../../../../lib/crtn.o
apogee@apogee-ubox:~/Code/testc$ 


```

here's some hint:
I have lines begin with:
```
COMPILER_PATH
LIBRARY_PATH
/usr/lib/gcc/i486-linux-gnu/4.4.3/collect2
```

---

### Post by DMacATTACK on 2011-06-13
ApOgEEs:

What do the line differences make? Do you know of a way to fix it?

---

### Post by ApOgEEs on 2011-06-14
Perhaps, I have library path. 

I haven't encounter this problem before. You can try re-install your gcc and see if there is any difference

---

### Post by DMacATTACK on 2011-06-17
I've tried:

$ sudo apt-get remove gcc

then

$ sudo apt-get install gcc


and theres no change in my problem

:(

$ gcc test.c -o run
$ ./run
bash: ./run: No such file or directory

---

### Post by ApOgEEs on 2011-06-17
try this:

$ sudo apt-get install build-essential

if you have it already installed, try:

$ sudo dpkg-reconfigure build-essential

then try again

---

### Post by DMacATTACK on 2011-06-24
I tried those, and no dice.

I did some searching and people who have had similar problems did this:

$ sudo apt-get install libc6-dev g++ gcc

But I still have no success.

---

### Post by DMacATTACK on 2011-07-04
I updated my Ubuntu from 10.04 to 11.04 and now my gcc is restored. Thanks for your help.

---

