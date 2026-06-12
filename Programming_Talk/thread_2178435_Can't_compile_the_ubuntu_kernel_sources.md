---
title: "Can't compile the ubuntu kernel sources"
date: 2013-10-03
forum: Programming Talk
---

### Post by Sidoney on 2013-10-03
I could install the ubuntu kernel sources with "apt-get source linux-image-$(uname -r)" and patch them with "zcat linux_3.8.0-31.46.diff.gz | patch -p0 2>&1 | tee patch.out" but i can't compile:

*  make oldconfig and make module_prepare work but report errors:
ubuntu/aufs/Kconfig:225:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:22:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:225:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:231:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:28:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:231:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:237:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:34:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:237:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:243:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:40:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:243:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:272:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:69:warning: choice value used outside its choice group
ubuntu/aufs/Kconfig:272:warning: choice value used outside its choice group

* make all ends with an error:
include/linux/wait.h:782:0: warning: "__wait_event_interruptible_lock_irq_timeout" redefined [enabled by default]
include/linux/wait.h:722:0: note: this is the location of the previous definition
  LD      mm/built-in.o

* make modules ends with an error:
include/linux/wait.h:782:0: warning: "__wait_event_interruptible_lock_irq_timeout" redefined [enabled by default]
include/linux/wait.h:722:0: note: this is the location of the previous definition
  LD [M]  drivers/iio/industrialio.o
make: *** [drivers] Error 2

I also tried it with the unpatched sources, but the errors do remain.
So it seems something is missing, although i never had such problems under OpenSuSE or Debian, but what? :confused:

---

### Post by GwL3eNC on 2013-10-04
Hello,

i would like to help you, but i don't know exactly what you are doing there with a patch. I would try the
kernel compilation in that way. You need 

sudo apt-get install linux-source build-essential kernel-package 

After that you can find the sources in

drwxr-xr-x 4 root root 4096 Mär 22 13:54 /usr/src/linux-source-ver3.2.1
lrwxrwxrwx 1 root root   45 Mär 20 01:07 /usr/src/linux-source-ver3.2.1.tar.bz2 -> linux-source-3.2.1/linux-source-3.2.1.tar.bz2

untar the package, change to the folder and use

cp /boot/config-`uname -r` .config 

to use your current kernel settings for the new one. Then
you can do 

yes "" | make oldconfig

and build a deb file using

make-kpkg --initrd buildpackage 

You can install the resulting deb file with

sudo dpkg -i linux-image-******.deb 

and proof after a system restart if the new kernel is running.

uname -a 

Greets

---

### Post by Sidoney on 2013-10-04
> **GwL3eNC said:**
> 

 use

cp /boot/config-`uname -r` .config 

to use your current kernel settings for the new one. Then
you can do 

yes "" | make oldconfig


That makes no sense because make oldconfig overrides the .config you copied before.
And i tried both versions of .config, but make all always ends with the same error :(


> **GwL3eNC said:**
> 
and build a deb file using

make-kpkg --initrd buildpackage 

You can install the resulting deb file with

sudo dpkg -i linux-image-******.deb 


I need no package, no other kernel, i only need some modified modules!
I only want to have some modifications to be active by compiling and loding modified modules.

For comparison i downloaded a kernel source from kernel.org and after make oldconfig i could compile the kernel and all modules without problems!
So there is a bug in the kernel sources from ubuntu and this also conflicts with the GPL.

---

### Post by Sidoney on 2013-10-05
I finally found the problem: It is necessary to start with

make distclean

because make clean or make mrproper is not enough.
So the problem is some trash in the ubuntu kernel sources.
After make distclean i could compile with

yes "" | make oldconfig 
make modules_prepare 
make -j2 all

---

