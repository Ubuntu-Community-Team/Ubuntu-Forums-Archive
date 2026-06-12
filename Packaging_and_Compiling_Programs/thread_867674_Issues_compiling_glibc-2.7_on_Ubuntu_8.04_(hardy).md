---
title: "Issues compiling glibc-2.7 on Ubuntu 8.04 (hardy)"
date: 2008-07-23
forum: Packaging and Compiling Programs
---

### Post by StoneSledge on 2008-07-23
I'm having issues compiling glibc-2.7 on Ubuntu 8.04 "Hardy". Please see "Issues:" further down.

Can someone please point out a valid and working configuration to create a complete build of glibc-2.7?

Thanks in advance!
Lars.


Attached are configuration, configuration log and make log files (logs-and-config-files.zip).

_Version info:_
Gcc:       4.2.3 (Ubuntu 4.2.3-2ubuntu7)
kernel:    2.6.24-19-generic
glibc-2.7 src: glibc_2.7-10ubuntu3.dsc (ubuntu source package)

_glibc-2.7 configure options:_
    --prefix=/usr/local/debug 
    --libexecdir=/usr/local/debug/glibc 
    --disable-profile 
    --enable-kernel=2.6.22 
    --without-gd 
    --without-selinux 
    --enable-shared 
    CC='gcc -m32 -march=i686 -mtune=native' 
    CXX='gcc -m32 -march=i686 -mtune=native' 
    CFLAGS='-O -g -fno-stack-protector' 


[U]Issues:
[/U]
gcc -m32 -march=i486  pthread_rwlock_trywrlock.c -c -std=gnu99 -fgnu89-inline -O -Wall -Winline -Wwrite-strings -fmerge-all-
constants -fno-stack-protector -g -Wstrict-prototypes -mpreferred-stack-boundary=2     -I../include -I/usr/src/glibc/glibc-b
uild/nptl -I/usr/src/glibc/glibc-build -I../sysdeps/i386/elf -I../nptl/sysdeps/unix/sysv/linux/i386/i686 -I../nptl/sysdeps/u
nix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux/i386 -I../nptl/sysdeps/unix/sysv/linux -I../nptl/sysdeps/pthread -I../sysde
ps/pthread -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/i
net -I../sysdeps/unix/sysv/i386 -I../nptl/sysdeps/unix/sysv -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../nptl/sysdeps/
unix -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../nptl/sysdeps/i386/i686 -I../sysdeps/i386/i686 -I..
/sysdeps/i386/i486 -I../nptl/sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../nptl/sysdeps/i386 -I../sysdeps/i386 -I../sysdeps/w
ordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sy
sdeps/generic/elf -I../sysdeps/generic -I../nptl  -I.. -I../libio -I. -I /lib/modules/2.6.24-19-generic/build/include -D_LIBC_REENTRANT -include ../include/libc-symbols.h   -DNOT_IN_libc=1 -DIS_IN_libpthread=1    -o /usr/src/glibc/glibc-build/nptl/pthread_rwlock_trywrlock.o -MD -MP -MF /usr/src/glibc/glibc-build/nptl/pthread_rwlock_trywrlock.o.dt -MT /usr/src/glibc/glibc-build/nptl/pthread_rwlock_trywrlock.o
[B]/tmp/ccBKuZj3.s: Assembler messages:
/tmp/ccBKuZj3.s:183: Error: suffix or operands invalid for `mov'
make[2]: *** [/usr/src/glibc/glibc-build/nptl/pthread_rwlock_tryrdlock.o] Error 1
[/B]

gcc -m32 -march=i486  ../nptl/sysdeps/unix/sysv/linux/i386/i686/pthread_rwlock_unlock.S -c  -I../include -I/usr/src/glibc/glibc-build/nptl -I/usr/src/glibc/glibc-build -I../sysdeps/i386/elf -I../nptl/sysdeps/unix/sysv/linux/i386/i686 -I../nptl/sysdeps/unix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux/i386 -I../nptl/sysdeps/unix/sysv/linux -I../nptl/sysdeps/pthread -I../sysdeps/pthread -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/inet -I../sysdeps/unix/sysv/i386 -I../nptl/sysdeps/unix/sysv -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../nptl/sysdeps/unix -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../nptl/sysdeps/i386/i686 -I../sysdeps/i386/i686 -I../sysdeps/i386/i486 -I../nptl/sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../nptl/sysdeps/i386 -I../sysdeps/i386 -I../sysdeps/wordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sysdeps/generic/elf -I../sysdeps/generic -I../nptl  -I.. -I../libio -I. -I /lib/modules/2.6.24-19-generic/build/include -D_LIBC_REENTRANT -include ../include/libc-symbols.h   -DNOT_IN_libc=1 -DIS_IN_libpthread=1    -DASSEMBLER  -DGAS_SYNTAX  -Wa,--noexecstack  -o /usr/src/glibc/glibc-build/nptl/pthread_rwlock_unlock.o -MD -MP -MF /usr/src/glibc/glibc-build/nptl/pthread_rwlock_unlock.o.dt -MT /usr/src/glibc/glibc-build/nptl/pthread_rwlock_unlock.o
[B]/tmp/ccw1P3A6.s: Assembler messages:
/tmp/ccw1P3A6.s:175: Error: suffix or operands invalid for `mov'
make[2]: *** [/usr/src/glibc/glibc-build/nptl/pthread_rwlock_trywrlock.o] Error 1
[/B]

[B]make[2]: Target `subdir_lib' not remade because of errors.
make[2]: Leaving directory `/usr/src/glibc/glibc-2.7/nptl'
[/B]

gcc -m32 -march=i486  pthread_rwlock_trywrlock.c -c -std=gnu99 -fgnu89-inline -O -Wall -Winline -Wwrite-strings -fmerge-all-
constants -fno-stack-protector -g -Wstrict-prototypes -mpreferred-stack-boundary=2     -I../include -I/usr/src/glibc/glibc-b
uild/nptl -I/usr/src/glibc/glibc-build -I../sysdeps/i386/elf -I../nptl/sysdeps/unix/sysv/linux/i386/i686 -I../nptl/sysdeps/u
nix/sysv/linux/i386 -I../sysdeps/unix/sysv/linux/i386 -I../nptl/sysdeps/unix/sysv/linux -I../nptl/sysdeps/pthread -I../sysde
ps/pthread -I../sysdeps/unix/sysv/linux -I../sysdeps/gnu -I../sysdeps/unix/common -I../sysdeps/unix/mman -I../sysdeps/unix/i
net -I../sysdeps/unix/sysv/i386 -I../nptl/sysdeps/unix/sysv -I../sysdeps/unix/sysv -I../sysdeps/unix/i386 -I../nptl/sysdeps/
unix -I../sysdeps/unix -I../sysdeps/posix -I../sysdeps/i386/i686/fpu -I../nptl/sysdeps/i386/i686 -I../sysdeps/i386/i686 -I..
/sysdeps/i386/i486 -I../nptl/sysdeps/i386/i486 -I../sysdeps/i386/fpu -I../nptl/sysdeps/i386 -I../sysdeps/i386 -I../sysdeps/w
ordsize-32 -I../sysdeps/ieee754/ldbl-96 -I../sysdeps/ieee754/dbl-64 -I../sysdeps/ieee754/flt-32 -I../sysdeps/ieee754 -I../sy
sdeps/generic/elf -I../sysdeps/generic -I../nptl  -I.. -I../libio -I. -I /lib/modules/2.6.24-19-generic/build/include -D_LIB
C_REENTRANT -include ../include/libc-symbols.h   -DNOT_IN_libc=1 -DIS_IN_libpthread=1    -o /usr/src/glibc/glibc-build/nptl/
pthread_rwlock_trywrlock.o -MD -MP -MF /usr/src/glibc/glibc-build/nptl/pthread_rwlock_trywrlock.o.dt -MT /usr/src/glibc/glib
c-build/nptl/pthread_rwlock_trywrlock.o
[B]/tmp/ccQkxQcS.s: Assembler messages:
/tmp/ccQkxQcS.s:183: Error: suffix or operands invalid for `mov'
/tmp/ccH39bkT.s: Assembler messages:
/tmp/ccH39bkT.s:175: Error: suffix or operands invalid for `mov'
make[2]: *** [/usr/src/glibc/glibc-build/nptl/pthread_rwlock_tryrdlock.o] Error 1
make[2]: *** [/usr/src/glibc/glibc-build/nptl/pthread_rwlock_trywrlock.o] Error 1
[/B]


[B]For more details please unzip and checkout attached logfiles (logs-and-config-files.zip)
[/B]

--

---

### Post by StoneSledge on 2008-07-24
Problem solved by extracting working build-params from the official ubuntu build logs.

You can use the code below to build script which generates a working configuration for glibc-2.7 on a i386 platform.

```
#
# Setup "configparams" which overrides the configuration script
#
cat > configparams <<-EOF
	CC = gcc-4.2 -fno-stack-protector
	CXX = g++-4.2 -fno-stack-protector
	BUILD_CC = gcc-4.2 -fno-stack-protector
	BUILD_CXX = g++-4.2 -fno-stack-protector
	CFLAGS = -pipe -O2 -fstrict-aliasing -g -mno-tls-direct-seg-refs
	BUILD_CFLAGS = -O2 -g
	BASH := /bin/bash
	KSH := /bin/bash
	LIBGD = no
	bindir = /usr/bin
	datadir = /usr/share
	localedir = /usr/lib/locale
	sysconfdir = /etc
	libexecdir = /usr/lib
	rootsbindir = /sbin
	includedir = /usr/include
	docdir = /usr/share/doc
	mandir = /usr/share/man
	sbindir = /usr/sbin
EOF

#
# Run glibc configuration script
#
CC="gcc-4.2 -fno-stack-protector" CXX="g++-4.2 -fno-stack-protector" AUTOCONF=false ../glibc-2.7/configure \
	--host=i486-linux-gnu \
	--build=i486-linux-gnu \
	--prefix=/usr/local/debug \
	--without-cvs \
	--enable-add-ons \
	--without-selinux \
	--enable-kernel=2.6.8  2>&1 | tee -a log-configure-glibc-2.7

#
# Now check for errors in "log-configure-glibc-2.7". 
# If no errors found, run make
#
# [COLOR="DarkRed"]**BEWARE: this example uses /usr/local/debug as prefix**[/COLOR]
#
```

--

---

### Post by darleys on 2008-08-01
StoneSledge
Can u please tell me the steps how u solved this iussue?

---

### Post by simo on 2008-10-03
Please tell me how to use this script...

I don't get it

---

### Post by Furquan on 2008-10-09
Hello Simo,
Just copy the whole script and paste it in your terminal keeping your present working directory as the directory where you are going to fire make..
Hope this helps you.:)

---

