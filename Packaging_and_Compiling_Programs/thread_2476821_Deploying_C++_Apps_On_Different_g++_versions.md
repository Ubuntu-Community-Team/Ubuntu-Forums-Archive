---
title: "Deploying C++ Apps On Different g++ versions"
date: 2022-07-08
forum: Packaging and Compiling Programs
---

### Post by flashc5 on 2022-07-08
Hello.  I have an interesting problem and curious what options are available.I do not have sudo on the server.  Degrading the dev machines g++ is not a option.// dev machine - gcc version 12.1.1 20220507 (Red Hat 12.1.1-1) (GCC) ```
g++ -vUsing built-in specs.COLLECT_GCC=/usr/bin/g++COLLECT_LTO_WRAPPER=/usr/libexec/gcc/x86_64-redhat-linux/12/lto-wrapperOFFLOAD_TARGET_NAMES=nvptx-noneOFFLOAD_TARGET_DEFAULT=1Target: x86_64-redhat-linuxConfigured with: ../configure --enable-bootstrap --enable-languages=c,c++,fortran,objc,obj-c++,ada,go,d,lto --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --with-bugurl=http://bugzilla.redhat.com/bugzilla --enable-shared --enable-threads=posix --enable-checking=release --enable-multilib --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-gnu-unique-object --enable-linker-build-id --with-gcc-major-version-only --enable-libstdcxx-backtrace --with-linker-hash-style=gnu --enable-plugin --enable-initfini-array --with-isl=/builddir/build/BUILD/gcc-12.1.1-20220507/obj-x86_64-redhat-linux/isl-install --enable-offload-targets=nvptx-none --without-cuda-driver --enable-offload-defaulted --enable-gnu-indirect-function --enable-cet --with-tune=generic --with-arch_32=i686 --build=x86_64-redhat-linux --with-build-config=bootstrap-lto --enable-link-serialization=1Thread model: posixSupported LTO compression algorithms: zlib zstdgcc version 12.1.1 20220507 (Red Hat 12.1.1-1) (GCC) 
```// server - gcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1) ```
g++ -vUsing built-in specs.COLLECT_GCC=g++COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/9/lto-wrapperOFFLOAD_TARGET_NAMES=nvptx-none:hsaOFFLOAD_TARGET_DEFAULT=1Target: x86_64-linux-gnuConfigured with: ../src/configure -v --with-pkgversion='Ubuntu 9.4.0-1ubuntu1~20.04.1' --with-bugurl=file:///usr/share/doc/gcc-9/README.Bugs --enable-languages=c,ada,c++,go,brig,d,fortran,objc,obj-c++,gm2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-9 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-9-Av3uEd/gcc-9-9.4.0/debian/tmp-nvptx/usr,hsa --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnuThread model: posixgcc version 9.4.0 (Ubuntu 9.4.0-1ubuntu1~20.04.1) 
```How can I deploy c++ executables on the server without installing/upgrading g++?Thanks in advance for any help you can give

---

### Post by TheFu on 2022-07-08
I would setup an LXD container and recreate the server setup with matching g++ and as much of the other environment as needed.  LXD can have a base OS that matches the server.  LXD can be treated like a VM for almost everything, with a few core kernel things not allows.

BTW, splitting up the compiler into separate lines for each option would help differences jump out.  Since I'm not being paid, I'll leave that to you. Too much like work, especially on a Friday.  I see a crapload of completely unnecessary options.  Simplifying that would be my 2nd step. I've never used or even seen most of those options before.

The other option is to statically link everything. The program will be huge, but it will be standalone.

BTW, Ubuntu doesn't support 32-bit (i686) in 20.04 and  later releases.

---

