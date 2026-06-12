---
title: "VMWare Xubuntu 8.4"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-05-27
Each time near the end of the VMWare setup i always get this error:

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:48:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.







What can i do in order to make this run properly?

---

### Post by quelx on 2008-05-27
You need the vmware-any-any patch 1.1.6 for the newer kernel, the answer is in the forums

---

### Post by nilsolaris on 2008-05-27
ALright and would you happen to have a link?

---

### Post by quelx on 2008-05-27
I searched for vmmon

[http://ubuntuforums.org/showthread.php?t=788169&highlight=vmmon](http://ubuntuforums.org/showthread.php?t=788169&highlight=vmmon)

---

### Post by HalPomeranz on 2008-05-27
You need a patch for the VMware source code.  I recommend following the instructions at:

[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)

---

### Post by nilsolaris on 2008-05-27
Highly confused, i apologize but can someone explain this a bit further?

---

### Post by nilsolaris on 2008-05-27
Im not actually sure on how to install this "vmware-any-any-update-116.tgz"

---

### Post by quelx on 2008-05-27
From the page HalPomeranz references

```
tar xf vmware-any-any-update-116.tgz
cd vmware-any-any-update116
sudo ./runme.pl
```

---

### Post by nilsolaris on 2008-05-27
Did so and got:

tar: vmware-any-any-update-116.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
cody@nilsolaris:~/vmware/vmware-server-distrib$ cd vmware-any-any-update116
bash: cd: vmware-any-any-update116: No such file or directory

---

### Post by nilsolaris on 2008-05-27
Alright i suppose this would be a better question... where should i place vmware-any-any-update-116.tgz in order to run it. (Again i apologize, new to linux, learning hands on)

---

### Post by quelx on 2008-05-27
If you downloaded the application from Firefox then it's on your **Desktop**

```
cd ~/Desktop
```

Then follow along the rest, tar xfvz, etc

---

