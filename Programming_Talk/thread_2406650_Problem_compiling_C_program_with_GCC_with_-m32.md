---
title: "Problem compiling C program with GCC with -m32"
date: 2018-11-23
forum: Programming Talk
---

### Post by a3ology on 2018-11-23
I'm trying to make a 32-bit program on a 64-bit system. To compile it I use ```
gcc  -v -m32 -L/usr/lib32/ -lX11 -lopenal -lm -lpthread -Ofast -o Unity src/Unity
```

This gives the following output:
```
Using built-in specs.COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/8/lto-wrapper
OFFLOAD_TARGET_NAMES=nvptx-none
OFFLOAD_TARGET_DEFAULT=1
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Debian 8.2.0-9' --with-bugurl=file:///usr/share/doc/gcc-8/README.Bugs --enable-languages=c,ada,c++,go,brig,d,fortran,objc,obj-c++ --prefix=/usr --with-gcc-major-version-only --program-suffix=-8 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-libmpx --enable-plugin --enable-default-pie --with-system-zlib --with-target-system-zlib --enable-objc-gc=auto --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 8.2.0 (Debian 8.2.0-9) 
COLLECT_GCC_OPTIONS='-v' '-L/usr/lib32/' '-m32' '-Ofast' '-o' 'Unity' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/x86_64-linux-gnu/8/cc1 -quiet -v -imultilib 32 -imultiarch i386-linux-gnu src/Unity.c -quiet -dumpbase Unity.c -m32 -mtune=generic -march=i686 -auxbase Unity -Ofast -version -o /tmp/ccUmbUbl.s
GNU C17 (Debian 8.2.0-9) version 8.2.0 (x86_64-linux-gnu)
    compiled by GNU C version 8.2.0, GMP version 6.1.2, MPFR version 4.0.1, MPC version 1.1.0, isl version isl-0.20-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
ignoring nonexistent directory "/usr/local/include/i386-linux-gnu"
ignoring nonexistent directory "/usr/lib/gcc/x86_64-linux-gnu/8/../../../../x86_64-linux-gnu/include"
#include "..." search starts here:
#include <...> search starts here:
 /usr/lib/gcc/x86_64-linux-gnu/8/include
 /usr/local/include
 /usr/lib/gcc/x86_64-linux-gnu/8/include-fixed
 /usr/include/i386-linux-gnu
 /usr/include
End of search list.
GNU C17 (Debian 8.2.0-9) version 8.2.0 (x86_64-linux-gnu)
    compiled by GNU C version 8.2.0, GMP version 6.1.2, MPFR version 4.0.1, MPC version 1.1.0, isl version isl-0.20-GMP


GGC heuristics: --param ggc-min-expand=100 --param ggc-min-heapsize=131072
Compiler executable checksum: 60e4cc17a994007a70b2cb653a475c93
COLLECT_GCC_OPTIONS='-v' '-L/usr/lib32/' '-m32' '-Ofast' '-o' 'Unity' '-mtune=generic' '-march=i686'
 as -v --32 -o /tmp/cclSRzB5.o /tmp/ccUmbUbl.s
GNU assembler version 2.31.1 (x86_64-linux-gnu) using BFD version (GNU Binutils for Debian) 2.31.1
COMPILER_PATH=/usr/lib/gcc/x86_64-linux-gnu/8/:/usr/lib/gcc/x86_64-linux-gnu/8/:/usr/lib/gcc/x86_64-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/8/:/usr/lib/gcc/x86_64-linux-gnu/
LIBRARY_PATH=/usr/lib/gcc/x86_64-linux-gnu/8/32/:/usr/lib/gcc/x86_64-linux-gnu/8/../../../../x86_64-linux-gnu/lib/../lib32/:/usr/lib/gcc/x86_64-linux-gnu/8/../../../i386-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/8/../../../../lib32/:/lib/i386-linux-gnu/:/lib/../lib32/:/usr/lib/i386-linux-gnu/:/usr/lib/../lib32/:/usr/lib/gcc/x86_64-linux-gnu/8/:/usr/lib/gcc/x86_64-linux-gnu/8/../../../../x86_64-linux-gnu/lib/:/usr/lib/gcc/x86_64-linux-gnu/8/../../../i386-linux-gnu/:/usr/lib/gcc/x86_64-linux-gnu/8/../../../:/lib/i386-linux-gnu/:/lib/:/usr/lib/i386-linux-gnu/:/usr/lib/
COLLECT_GCC_OPTIONS='-v' '-L/usr/lib32/' '-m32' '-Ofast' '-o' 'Unity' '-mtune=generic' '-march=i686'
 /usr/lib/gcc/x86_64-linux-gnu/8/collect2 -plugin /usr/lib/gcc/x86_64-linux-gnu/8/liblto_plugin.so -plugin-opt=/usr/lib/gcc/x86_64-linux-gnu/8/lto-wrapper -plugin-opt=-fresolution=/tmp/ccCqrL3P.res -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s -plugin-opt=-pass-through=-lc -plugin-opt=-pass-through=-lgcc -plugin-opt=-pass-through=-lgcc_s --sysroot=/ --build-id --eh-frame-hdr -m elf_i386 --hash-style=gnu -dynamic-linker /lib/ld-linux.so.2 -pie -o Unity /usr/lib/gcc/x86_64-linux-gnu/8/../../../../lib32/Scrt1.o /usr/lib/gcc/x86_64-linux-gnu/8/../../../../lib32/crti.o /usr/lib/gcc/x86_64-linux-gnu/8/32/crtbeginS.o -L/usr/lib32/ -L/usr/lib/gcc/x86_64-linux-gnu/8/32 -L/usr/lib/gcc/x86_64-linux-gnu/8/../../../../x86_64-linux-gnu/lib/../lib32 -L/usr/lib/gcc/x86_64-linux-gnu/8/../../../i386-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/8/../../../../lib32 -L/lib/i386-linux-gnu -L/lib/../lib32 -L/usr/lib/i386-linux-gnu -L/usr/lib/../lib32 -L/usr/lib/gcc/x86_64-linux-gnu/8 -L/usr/lib/gcc/x86_64-linux-gnu/8/../../../../x86_64-linux-gnu/lib -L/usr/lib/gcc/x86_64-linux-gnu/8/../../../i386-linux-gnu -L/usr/lib/gcc/x86_64-linux-gnu/8/../../.. -L/lib/i386-linux-gnu -L/usr/lib/i386-linux-gnu -lX11 -lm -lpthread -lopenal /tmp/cclSRzB5.o -lgcc --push-state --as-needed -lgcc_s --pop-state -lc -lgcc --push-state --as-needed -lgcc_s --pop-state /usr/lib/gcc/x86_64-linux-gnu/8/32/crtfastmath.o /usr/lib/gcc/x86_64-linux-gnu/8/32/crtendS.o /usr/lib/gcc/x86_64-linux-gnu/8/../../../../lib32/crtn.o
/usr/bin/ld: skipping incompatible //usr/lib/x86_64-linux-gnu/libX11.so when searching for -lX11
/usr/bin/ld: skipping incompatible //usr/lib/x86_64-linux-gnu/libX11.a when searching for -lX11
/usr/bin/ld: cannot find -lX11
collect2: error: ld returned 1 exit status
```

It skips the needed library because it is "incompatible". I have installed gcc-multilib, all the needed 32-bit libraries, and a bunch of other stuff I probably don't need just to get this to work. Any help would be greatly appreciated as this is a very big project for me.

---

### Post by dwhitney67 on 2018-11-24
Try installing the 32-bit versions of the X11 libraries:
```

$ sudo apt-get install libx11-6:i386

```

---

