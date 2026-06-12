---
title: "Shared libraries are not linked to the binary"
date: 2012-01-13
forum: Packaging and Compiling Programs
---

### Post by elrafapadron on 2012-01-13
I am getting weird results after compiling the code shown below: 
 
$ g++ -rdynamic -o ../../kernel kernel.cpp.o [COLOR=red]../../lib/led.so ../../lib/remote.so[/COLOR] -L"../../lib" -lcore -ldl 
 
$ ldd ../../kernel linux-gate.so.1 => (0x0059c000)
[COLOR=red]../../lib/led.so (0x00b2a000)[/COLOR]
libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x00ed5000)
libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0x0089d000)
libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0x00d84000)
libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00143000)
/lib/ld-linux.so.2 (0x00c26000)
libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x00110000)
 
$ g++ -rdynamic -o ../../kernel kernel.cpp.o [COLOR=red]../../lib/remote.so ../../lib/led.so[/COLOR] -L"../../lib" -lcore -ldl 
 
$ ldd ../../kernel linux-gate.so.1 => (0x006e7000)
**[COLOR=red]../../lib/remote.so (0x00e6e000)[/COLOR]**
libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0x00a15000)
libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0x0027c000)
libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0x00716000)
libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0x00367000)
/lib/ld-linux.so.2 (0x001fc000)
libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0x008ed000)
 
$ g++ -v
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/gcc/i686-linux-gnu/4.5.4/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.3-9ubuntu1' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.4 (Ubuntu/Linaro 4.5.3-9ubuntu1)
 
I am not able to load both shared libraries at the same time. 
 
Please, Could any one tell me how to link multiple share libraries to the same binary?

---

### Post by MadCow108 on 2012-01-14
do the libraries have circular dependencies?
it seems like they do, so the ordering on the commandline depends which library is actually linked with.
This is due to the as-needed flag which only links what is needed.

try adding the libraries multiple times to the command line so the circular references can be resolved:
```
gcc .. liba libb liba
```

or disable as-needed with: 
```
gc -Wl,--no-as-needed ... liba libb
```

I also recommend using -Wl,--no-undefined to ensure that the binary is self sufficient.
(ldd -r will also tell you that afterwards)

---

### Post by elrafapadron on 2012-01-16
Thank you very much!!!! you made my week :)

---

