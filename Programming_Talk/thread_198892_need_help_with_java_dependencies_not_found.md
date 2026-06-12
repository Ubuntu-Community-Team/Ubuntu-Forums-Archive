---
title: "need help with java dependencies not found"
date: 2006-06-17
forum: Programming Talk
---

### Post by m0rd on 2006-06-17
Hey all, been playing around with Ubuntu for about a month now, and liking it
But I've come across a problem here. I'm trying to use lwjgl to do some games programming, but can't get it to run. I tried the lwjgl forums but we've come to a point where they don't know what is wrong. Anyway here is some output.

mord@neo:~/Desktop/LWJGL/lwjgl/native/linux$ ldd liblwjgl.so
linux-gate.so.1 => (0xffffe000)
libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7efa000)
libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e14000)
libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e07000)
libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7df5000)
libjawt.so => not found
libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7cc5000)
/lib/ld-linux.so.2 (0x80000000)
libXau.so.6 => /usr/lib/libXau.so.6 (0xb7cc2000)
libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7cbf000)

libjawt.so is where the problem is. When I do "ldconfig -p " it shows this:

libjawt.so (libc6, hwcap: 0x1000000000000) => /usr/lib/j2sdk1.5-sun/jre/lib/i386/libjawt.so

i think that means it is loaded

little clueless here though

any help that i can get would be appreciated .

Don't really wanna go back to windows if I don't have to

thanks

---

### Post by ThorPrime on 2006-06-20
I'm in the same boat.
I need to get a linux box up for LWGJL development but I too get:

$ ldd liblwjgl.so
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib32/libm.so.6 (0x55598000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x555ba000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x556a0000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x556ad000)
        libjawt.so => not found
        libc.so.6 => /lib32/libc.so.6 (0x556c0000)
        /lib/ld-linux.so.2 (0x56555000)
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x557ef000)
        libdl.so.2 => /lib32/libdl.so.2 (0x557f2000)

---

