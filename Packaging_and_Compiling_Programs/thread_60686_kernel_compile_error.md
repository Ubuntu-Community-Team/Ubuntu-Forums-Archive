---
title: "kernel compile error"
date: 2005-08-28
forum: Packaging and Compiling Programs
---

### Post by diablo2007 on 2005-08-28
Upon doing any of the following:
make-kpkg kernel_image
make-kpkg --initrd kernel_image
make bzImage

i recieve the following

drivers/built-in.o(.text+0x6fa98): In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o(.text+0x2847): first defined here
ld: Warning: size of symbol `dump_stack' changed from 22 in arch/i386/kernel/built-in.o to 37 in drivers/built-in.o
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
make: *** [stamp-build] Error 2

---

### Post by ErikDeBruijn on 2005-12-13
**SOLVED by removing ndiswrapper!**

In a struggle to get hibernation working and at the same time the proprietary nvidia driver working, I needed to compile my own kernel. 

I'm having the same error output here, but now with 2.6.12 (the ubuntu tree). It seems more people (even today) are having this problem: [http://ubuntuforums.org/showthread.php?t=15235](http://ubuntuforums.org/showthread.php?t=15235)

I've applied the suspend2 patches following the instructions here: 
[http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2)

I've tried a lot of configurations, done a make clean, but this build problem seems very persistent.

```
 LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o:(.bss+0x96f4): multiple definition of `debug'
arch/i386/kernel/built-in.o:: first defined here
drivers/built-in.o: In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o:: first defined here
ld: Warning: size of symbol `dump_stack' changed from 22 in arch/i386/kernel/built-in.o to 37 in drivers/built-in.o
make: *** [.tmp_vmlinux1] Error 1

```

I'm using gcc 3.4, or more precisely:
root@acerik:/usr/src/linux # $CC -v
Reading specs from /usr/lib/gcc/i486-linux-gnu/3.4.5/specs
Configured with: ../src/configure -v --enable-languages=c,c++,f77,pascal,objc,ada --prefix=/usr --libexecdir=/usr/lib --with-gxx-include-dir=/usr/include/c++/3.4 --enable-shared --with-system-zlib --enable-nls --without-included-gettext --program-suffix=-3.4 --enable-__cxa_atexit --enable-libstdcxx-allocator=mt --enable-clocale=gnu --enable-libstdcxx-debug i486-linux-gnu
Thread model: posix
gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)

If anyone needs it: this is my patch to the nvidia installer:
```
3853a3854,3856
>       case PM_SUSPEND_STANDBY:
>             nv_printf(NV_DBG_INFO, "NVRM: ACPI: received standby event **KERNEL MODULE CHANGE BY ERIK DE BRUIJN**\n");

```

**I've made some modules under USB built in, but not all have to be built-in. I've unset ndiswrapper, after that it WORKED!**

Also posted here: [http://ubuntuforums.org/showthread.php?t=15235](http://ubuntuforums.org/showthread.php?t=15235)

---

### Post by wbaguhn on 2007-04-12
setting ndiswrapper to compile as a module was helpful for me.

(error occurred when set to "yes" inadvertently)

---

