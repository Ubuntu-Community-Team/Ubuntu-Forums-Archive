---
title: "Cant compile using libsensors4"
date: 2010-11-24
forum: Packaging and Compiling Programs
---

### Post by AlmightyJu on 2010-11-24
Hi Guys,

I hope someone can help because im running out of ideas!!

I'm making a program in c++ that accesses temperature data from lm-sensors and I cant compile it, I have libsensors4, libsensors4-dev and lm-sensors installed.

This is the output:
```
julian@Julian-Linux:~/LCDScreenApp$ g++ main.cpp -v -o ./bin/Debug/main
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) 
COLLECT_GCC_OPTIONS='-v' '-o' './bin/Debug/main' '-shared-libgcc' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/cc1plus -quiet -v -D_GNU_SOURCE main.cpp -D_FORTIFY_SOURCE=2 -quiet -dumpbase main.cpp -mtune=generic -auxbase main -version -fstack-protector -o /tmp/cci7Dpk6.s
ignoring nonexistent directory "/usr/local/include/x86_64-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../x86_64-linux-gnu/include"
ignoring nonexistent directory "/usr/include/x86_64-linux-gnu"
#include "..." search starts here:
#include <...> search starts here:
 /usr/include/c++/4.4
 /usr/include/c++/4.4/x86_64-linux-gnu
 /usr/include/c++/4.4/backward
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/include
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/include-fixed
 /usr/include
End of search list.
GNU C++ (Ubuntu/Linaro 4.4.4-14ubuntu5) version 4.4.5 (x86_64-linux-gnu)
	compiled by GNU C version 4.4.5, GMP version 4.3.2, MPFR version 3.0.0-p3.
GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: b408a5c1addf39d3fcc1ff19852f1cfe
COLLECT_GCC_OPTIONS='-v' '-o' './bin/Debug/main' '-shared-libgcc' '-mtune=generic'
 as -V -Qy -o /tmp/cczu9J03.o /tmp/cci7Dpk6.s
GNU assembler version 2.20.51 (x86_64-linux-gnu) using BFD version (GNU Binutils for Ubuntu) 2.20.51-system.20100908
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/:/lib/../lib/:/usr/lib/../lib/:/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../:/lib/:/usr/lib/:/usr/lib/x86_64-linux-gnu/
COLLECT_GCC_OPTIONS='-v' '-o' './bin/Debug/main' '-shared-libgcc' '-mtune=generic'
 /usr/lib/gcc/x86_64-linux-gnu/4.4.5/collect2 --build-id --eh-frame-hdr -m elf_x86_64 --hash-style=gnu -dynamic-linker /lib64/ld-linux-x86-64.so.2 -o ./bin/Debug/main -z relro /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crt1.o /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crti.o /usr/lib/gcc/x86_64-linux-gnu/4.4.5/crtbegin.o -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5 -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib -L/lib/../lib -L/usr/lib/../lib -L/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../.. -L/usr/lib/x86_64-linux-gnu /tmp/cczu9J03.o -lstdc++ -lm -lgcc_s -lgcc -lc -lgcc_s -lgcc /usr/lib/gcc/x86_64-linux-gnu/4.4.5/crtend.o /usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crtn.o
/tmp/cczu9J03.o: In function `main':
main.cpp:(.text+0x515): undefined reference to `sensors_init'
main.cpp:(.text+0x53c): undefined reference to `sensors_parse_chip_name'
main.cpp:(.text+0x584): undefined reference to `sensors_get_label'
main.cpp:(.text+0x5d3): undefined reference to `sensors_get_subfeature'
main.cpp:(.text+0x612): undefined reference to `sensors_get_value'
main.cpp:(.text+0x670): undefined reference to `sensors_get_features'
collect2: ld returned 1 exit status

```

If i remove libsensors4-dev i get the error
main.cpp:12: fatal error: sensors/sensors.h: No such file or directory

so its finding the headers but it just wont compile and I cant understand it. 

anyone have any ideas or could they try compiling the attached to see if it works?

Thanks!
Ju

---

### Post by SevenMachines on 2010-11-24
You need to link to the sensors library too
$ g++ main.cpp -v -o ./bin/Debug/main -lsensors

---

### Post by AlmightyJu on 2010-11-24
:o so simple!! for future reference how do you find out that you need to do that sort of thing?? i couldn't find it in the manpage or anything!

---

### Post by SevenMachines on 2010-11-24
It should be mentioned in most gcc tutorials i imagine, if you use an outside library you'll need to tell the linker to link to it.

---

