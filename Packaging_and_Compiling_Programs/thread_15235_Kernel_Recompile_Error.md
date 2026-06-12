---
title: "Kernel Recompile Error"
date: 2005-02-13
forum: Packaging and Compiling Programs
---

### Post by iotc247 on 2005-02-13
Upon doing make-kpkg i get


```

 LD      .tmp_vmlinux1
drivers/built-in.o(.text+0x80ea0): In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o(.text+0x2e80): first defined here
ld: Warning: size of symbol `dump_stack' changed from 32 in arch/i386/kernel/bui lt-in.o to 51 in drivers/built-in.o
drivers/built-in.o(.text+0x781fc): In function `unload_ndis_driver':
: undefined reference to `usb_deregister'
drivers/built-in.o(.text+0x785c9): In function `start_driver':
: undefined reference to `usb_register'
drivers/built-in.o(.text+0x828fd): In function `usb_transfer_complete_tasklet':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x82a80): In function `usb_cancel_worker':
: undefined reference to `usb_kill_urb'
drivers/built-in.o(.text+0x82a8f): In function `usb_cancel_worker':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x82b4c): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_alloc_urb'
drivers/built-in.o(.text+0x82cb0): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x82ce7): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x82d2b): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x82e6c): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_alloc_urb'
drivers/built-in.o(.text+0x82f4f): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x82f91): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x83032): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x831d8): In function `usb_submit_nt_urb':
: undefined reference to `usb_set_interface'
drivers/built-in.o(.text+0x831f6): In function `usb_submit_nt_urb':
: undefined reference to `usb_ifnum_to_if'
drivers/built-in.o(.text+0x8333c): In function `usb_submit_nt_urb':
: undefined reference to `usb_get_descriptor'
drivers/built-in.o(.text+0x8340b): In function `usb_reset_port':
: undefined reference to `usb_reset_device'
drivers/built-in.o(.text+0x830fa): In function `usb_reset_pipe':
: undefined reference to `usb_clear_halt'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
make: *** [stamp-build] Error 2
alex@alexs-lappy:/usr/src/linux-source-2.6.10 $

```

My conf is attached.

---

### Post by iotc247 on 2005-02-13
Ok well now i only have the dump_stack part of the error... So anyone?

---

### Post by diablo2007 on 2005-08-28
I am having a similair dump_stack error as well.

---

### Post by ErikDeBruijn on 2005-12-13
**SOLVED by removing ndiswrapper!**
I believe I had this module built-in.

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

[http://ubuntuforums.org/showthread.php?p=571550#post571550](http://ubuntuforums.org/showthread.php?p=571550#post571550)

--
Regards,

Erik de Bruijn
[http://www.budgetdedicated.com/solutions.php](http://www.budgetdedicated.com/solutions.php)

---

