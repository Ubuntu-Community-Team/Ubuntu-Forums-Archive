---
title: "error while building a tool chain"
date: 2006-09-12
forum: Programming Talk
---

### Post by mtnbkr on 2006-09-12
I'm newbie trying to learn embedded linux programming. I'm trying to build a cross platform toolchain (using Ubuntu kernel 2.6.15-26-686 kernel) for an arm processor cirrus logic ep-9302 but I kept getting the error below. Any idea how to fix it. Thanks in advance.

[email]mtnbkr@speed:~/buildArmlinux/BUILD/gcc-3.4.4.buil[/email]d-1$ ../gcc-3.4.4/configure \
> --prefix=${PREFIX} \
> --host=i686-pc-linux-gnu \
> --target=${TARGET} \
> --disable-shared \
> --disable-threads \
> --enable-languages=c \
> --disable-multilib \
> --disable-nls \
> --enable-symvers=gnu \
> --enable-__cxa_atexit \
> --with-local-prefix=${PREFIX}
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... arm-unknown-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
*** This configuration is not supported in the following subdirectories:
     target-libstdc++-v3 target-libf2c target-libffi target-boehm-gc target-zlib target-libjava zlib fastjar target-libobjc
    (Any other directories should still work fine.)
checking for i686-pc-linux-gnu-ar... no
checking for ar... ar
checking for i686-pc-linux-gnu-as... no
checking for as... as
checking for i686-pc-linux-gnu-dlltool... no
checking for dlltool... dlltool
checking for i686-pc-linux-gnu-ld... no
checking for ld... ld
checking for i686-pc-linux-gnu-nm... no
checking for nm... nm
checking for i686-pc-linux-gnu-ranlib... no

---

