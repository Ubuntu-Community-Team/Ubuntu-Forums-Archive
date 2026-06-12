---
title: "vmware para-virtualising modules wont compile"
date: 2007-02-13
forum: Programming Talk
---

### Post by puccaso on 2007-02-13
okay

i dont get any of this
i remmeber seeing some sort of fix for this
i remember even figuring it out ONCE but oh gosh i need help

this is the output
```


Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmmon-only'
make -C /lib/modules/2.6.20-8-lowlatency/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-8-lowlatency'
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.c:80:
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘compat_exit’
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or ‘...’ before ‘exit_code’
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to ‘int’ in declaration of ‘_syscall1’
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-8-lowlatency'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
```


why is it being difficult???

---

### Post by vigleik on 2007-02-13
Just a shot in the dark, but did you try a different (earlier) version of the c compiler?

---

### Post by puccaso on 2007-02-13
yes
4.1 and 4.

and 3.5


i remember the problem are to do with files in the vmmon and vmnet tar's that contain the source for the modules..

something to do with declare something?

---

