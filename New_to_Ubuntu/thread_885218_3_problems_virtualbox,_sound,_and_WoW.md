---
title: "3 problems: virtualbox, sound, and WoW"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by purplearcanist on 2008-08-09
I try to run VirtualBox, and it tells me to recompile the kernel.  Here is what I get when I try:


eliot@dell:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                                 
 * Look at /var/log/vbox-install.log to find out what went wrong
eliot@dell:~$ cat /var/log/vbox-install.log
cp: missing destination file operand after `/tmp/vbox.0/Module.symvers'
Try `cp --help' for more information.
make KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/tmp/vbox.0 SRCROOT=/tmp/vbox.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/vbox.0/.tmp_versions ; rm -f /tmp/vbox.0/.tmp_versions/*
make -f scripts/Makefile.build obj=/tmp/vbox.0
  gcc -m32 -Wp,-MD,/tmp/vbox.0/linux/.SUPDrv-linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/lib/modules/2.6.24-16-generic/build/include  -I/tmp/vbox.0/ -I/tmp/vbox.0/include -I/tmp/vbox.0/r0drv/linux -D__KERNEL__ -DMODULE -D__LINUX__ -DIN_RING0 -DIN_RT_R0 -DIN_SUP_R0 -DCONFIG_VBOXDRV_AS_MISC -D__X86__   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(SUPDrv_linux)"  -D"KBUILD_MODNAME=KBUILD_STR(vboxdrv)" -c -o /tmp/vbox.0/linux/.tmp_SUPDrv-linux.o /tmp/vbox.0/linux/SUPDrv-linux.c
In file included from /tmp/vbox.0/include/iprt/types.h:55,
                 from /tmp/vbox.0/include/VBox/types.h:25,
                 from /tmp/vbox.0/SUPDRV.h:31,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:24:
include/linux/types.h:40: error: redefinition of typedef ‘uintptr_t’
/tmp/vbox.0/include/iprt/stdint.h:119: error: previous declaration of ‘uintptr_t’ was here
In file included from include/linux/thread_info.h:33,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from /tmp/vbox.0/SUPDRV.h:84,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:24:
include/linux/bitops.h:6:1: warning: "BIT" redefined
In file included from /tmp/vbox.0/include/VBox/cdefs.h:24,
                 from /tmp/vbox.0/SUPDRV.h:30,
                 from /tmp/vbox.0/linux/SUPDrv-linux.c:24:
/tmp/vbox.0/include/iprt/cdefs.h:979:1: warning: this is the location of the previous definition
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 1
make[1]: *** [_module_/tmp/vbox.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vboxdrv] Error 2

Another problem is that the sound does not work.  How can I fix this?

Also, is there a good guide for installing world of warcraft?

I am running Hardy Heron with a Dell Inspiron 1420 preloaded with Ubuntu (when those computers first came out)

---

### Post by pi.boy.travis on 2008-08-09
Wow will install easily with WINE, more info on their website.  Could we get some system specs in regards to your sound problem?

---

### Post by purplearcanist on 2008-08-09
> **pi.boy.travis said:**
> Wow will install easily with WINE, more info on their website.  Could we get some system specs in regards to your sound problem?

Sound is up and running.:)

Followed this guide:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Modem_Does_Not_Work)

---

### Post by purplearcanist on 2008-08-10
tap

---

### Post by purplearcanist on 2008-08-16
tap tap

---

