---
title: "vmware compiling error"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Dev'olution on 2008-10-21
```
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:53:
/tmp/vmware-config0/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:16:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:84:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config0/vmmon-only/linux/driver.c:171: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c:175: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config0/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config0/vmmon-only/linux/driver.c: In function ‘__LinuxDriver_Ioctl’:
/tmp/vmware-config0/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

Whats wrong here i've gotten the build-essential files and the libraries for my kernel... i'm running 8.10 beta ftr.

---

### Post by Ctrl+Alt+Del on 2008-10-21
assuming you are trying to install ws 6.5... iirc currently there is a problem with kernel 2.6.27... I remember reading sth along the lines on the gentoo bugtracker

---

### Post by hyper_ch on 2008-10-21
have a read through ehre: [https://bugs.launchpad.net/ubuntu/+bug/263837](https://bugs.launchpad.net/ubuntu/+bug/263837) and you will be provided with a bug (and rudimentary install instructions by me)

---

