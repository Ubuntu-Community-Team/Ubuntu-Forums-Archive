---
title: "Vmware server having vmmon module problems"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by silent contender on 2008-11-29
When I run sudo vmware-config.pl, I get this:

```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.27-9-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/paravirt.h:7,
                 from include/asm/irqflags.h:55,
                 from include/linux/irqflags.h:57,
                 from include/asm/system.h:11,
                 from include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:71:
/tmp/vmware-config1/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config1/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```

How do I fix this.  I am using VMware Server 1.06, Ubuntu 8.10

Thanks.

---

### Post by drifting on 2008-11-30
Same thing, running 64 Bit Ultimate and Ver 2 VMware server. Tried the patch that was knocking around from similar problems a while back, but that made no difference (That was an act of desperation as I needed to read my work email in Outlook)

---

### Post by ben_l on 2008-11-30
I'm having the exact same issue.  I can't recompile VMWare.  Is there some trick to this?  Does something need to be entered, other than the default for this question?

[B]What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-9-generic/build/include][/B]

---

### Post by drifting on 2008-12-01
Mmm, nothing daft like your missing the linux-headers for your Kernel? Not as if I know what I am talking about, just a wild stab in the dark.

Paul.

---

### Post by hyper_ch on 2008-12-01
Have a look at: [https://bugs.launchpad.net/ubuntu/+bug/263837/comments/36](https://bugs.launchpad.net/ubuntu/+bug/263837/comments/36)  and [https://bugs.launchpad.net/ubuntu/+bug/263837/comments/34](https://bugs.launchpad.net/ubuntu/+bug/263837/comments/34) (or browse through the whole bug report: [https://bugs.launchpad.net/ubuntu/+bug/263837](https://bugs.launchpad.net/ubuntu/+bug/263837) )

---

### Post by ben_l on 2008-12-01
Very nice.  That patch works for me.  Not sure why I didn't think to try that, as I also had to use it the first time around.  Thanks for pointing me in the right direction!

---

