---
title: "VMWare Player"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by General Specific on 2008-05-25
How do I load VMware player.

I downloaded it and now I'm lost.

---

### Post by scizzo on 2008-05-25
You downloaded it from the website?

I believe there is install instructions for it on the site also.

---

### Post by shifty_powers on 2008-05-25
virtualbox, which is available in deb form, would probably be easier...

---

### Post by General Specific on 2008-05-25
You would thing that VMWare would have instructions, but they don't.

I found the install.pl file and ran it sudo.  It was all going well when I hit this snag:



Building the vmmon module.



Using 2.6.x kernel build system.

make: Entering directory `/tmp/vmware-config0/vmmon-only'

make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'

  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o

  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o

  CC [M]  /tmp/vmware-config0/vmmon-only/common/comport.o

  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o

In file included from include/asm/bitops.h:2,

                 from /tmp/vmware-config0/vmmon-only/./include/vcpuset.h:74,

                 from /tmp/vmware-config0/vmmon-only/./include/modulecall.h:23,

                 from /tmp/vmware-config0/vmmon-only/common/vmx86.h:18,

                 from /tmp/vmware-config0/vmmon-only/common/hostif.h:18,

                 from /tmp/vmware-config0/vmmon-only/common/cpuid.c:14:

include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly

make[2]: *** [/tmp/vmware-config0/vmmon-only/common/cpuid.o] Error 1

make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'

make: *** [vmmon.ko] Error 2

make: Leaving directory `/tmp/vmware-config0/vmmon-only'

Unable to build the vmmon module.



For more information on how to troubleshoot module-related problems, please 

visit our Web site at "http://www.vmware.com/download/modules/modules.html" and

"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".



any ideas?

---

### Post by shifty_powers on 2008-05-25
yes, use virtualbox. for the most part it is a lot easier to use andinstall and will do everything that you need ;)

---

### Post by General Specific on 2008-05-25
> **shifty_powers said:**
> virtualbox, which is available in deb form, would probably be easier...


Will VirtualBox run a VMC file.

I have an XP.vmc that I want to run.

---

### Post by shifty_powers on 2008-05-25
heh no but

[http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware](http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware)

is a very good tutorial for installing vmware.

used it myself, though i use virtualbox now ;)

---

### Post by lazyart on 2008-05-25
Thread for installing vmware server is [here]("http://ubuntuforums.org/showthread.php?t=788169&highlight=vmware+howto").

---

### Post by cosine352 on 2008-05-25
virtual box is faster and easier.

---

### Post by shifty_powers on 2008-05-25
but pointless if, as the op has stated, he wts to run an existing vmware virtual machine that he has...

---

### Post by General Specific on 2008-05-25
It's OK, I can reload XP.

---

