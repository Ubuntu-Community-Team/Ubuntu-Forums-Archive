---
title: "Missing include when cross-compiling a 64 bit program on Ubuntu 10.10 x86"
date: 2011-03-11
forum: Packaging and Compiling Programs
---

### Post by pedro.daquino on 2011-03-11
Hi,

I've come across the same problem as this StackOverflow member: [http://stackoverflow.com/questions/4643197/missing-include-bits-cconfig-h-when-cross-compiling-64-bit-program-on-32-bit](http://stackoverflow.com/questions/4643197/missing-include-bits-cconfig-h-when-cross-compiling-64-bit-program-on-32-bit).

In a nutshell, I cannot compile the following program with g++ -m64:

```
pfranco@pfranco:~/Desktop$ cat test.cpp 
#include <iostream>

int main( int argc, char** argv )
{
  std::cout << "hello world" << std::endl;
  return 0;
}
pfranco@pfranco:~/Desktop$ g++ -m64 teste.cpp
In file included from test.cpp:1:
/usr/include/c++/4.4/iostream:39: fatal error: bits/c++config.h: No such file or directory
compilation terminated.
pfranco@pfranco:~/Desktop$ g++ -v
Using built-in specs.
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.4.4-14ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.4 --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --libdir=/usr/lib --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)
```

There are two "solutions" on that SO question, both rather hackish. I wonder if this is a bug on Ubuntu, or if I'm missing a package. I've already installed g++-4.4-multilib.

Thanks in advance.

---

