---
title: "g++ config issue"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by kaliyugantagonist on 2012-07-17
Hello,

I am trying to install hpcc which has a dependency on g++ package :

dpkg: dependency problems prevent configuration of hpccsystems-platform:
 [B]hpccsystems-platform depends on g++; however:
  Package g++ is not configured yet[/B].
dpkg: error processing hpccsystems-platform (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hpccsystems-platform

Hence, I referred to [http://ubuntuguide.net/how-to-install-and-setup-gcc-4-1g4-1-in-ubuntu-10-0410-10 ]("http://ubuntuguide.net/how-to-install-and-setup-gcc-4-1g4-1-in-ubuntu-10-0410-10")

When I do **gcc -v** :

gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/lto-wrapper
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=x86_64-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/x86_64-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/x86_64-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4)

When I execute **ls /usr/bin/gcc*** :

/usr/bin/gcc  /usr/bin/gcc-4.5

The link I referred to has confused me regarding the 'alternatives'.

[COLOR=Red]**I had installed g++ from the pool directory of the repository present on the VM provided to me - it has no Internet connectivity !**[/COLOR]

Please guide as to how I should proceed.

Thanks and regards !

---

