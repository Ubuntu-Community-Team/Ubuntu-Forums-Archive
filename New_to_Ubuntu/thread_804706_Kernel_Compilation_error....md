---
title: "Kernel Compilation error..."
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jemate18 on 2008-05-23
Hi everyone!

Im using Xubuntu Hardy with 2.6.24-16 kernel (generic?)

I'm practicing how to compile my kernel so i tried this as root

1. $make menuconfig //after exiting here is the output
```
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
  HOSTCC  scripts/kconfig/lxdialog/inputbox.o
  HOSTCC  scripts/kconfig/lxdialog/menubox.o
  HOSTCC  scripts/kconfig/lxdialog/textbox.o
  HOSTCC  scripts/kconfig/lxdialog/util.o
  HOSTCC  scripts/kconfig/lxdialog/yesno.o
  HOSTCC  scripts/kconfig/mconf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
scripts/kconfig/mconf arch/x86/Kconfig
#
# configuration written to .config
#

*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

```

2. $make dep //here is the output
```
 HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
*** Warning: make dep is unnecessary now.

```

3. $make clean //here is the output
```
CLEAN   .tmp_versions

```

4 $make bzImage //here is the ERROR!
```
 CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[1]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2

```
  
Please help.. I don't know the reason why this happened.
I searched the forum and found 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/233950](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/233950)

There is no respond yet

Thanks

---

### Post by dark0dave on 2008-05-29
I have the same problem try [http://kanotix.com/files/debian/pool/main/a/acerhk/](http://kanotix.com/files/debian/pool/main/a/acerhk/) and get the debs! This will hopefully work, good luck
:KS

---

### Post by jemate18 on 2008-06-06
> **dark0dave said:**
> I have the same problem try [http://kanotix.com/files/debian/pool/main/a/acerhk/](http://kanotix.com/files/debian/pool/main/a/acerhk/) and get the debs! This will hopefully work, good luck
:KS

Hey. Thanks a lot. It work, but I was hoping to compile
my kernel using the methods I have listed above so that I could learn the step by step process of it. The method you gave me really works, only problem is that it is like, an automatic thing much like of an apt-get install vs. ./configure, make && make install.

Thanks again.

---

### Post by sdennie on 2008-06-06
I understand you said you wanted to use the "raw" method of building a kernel but, there are much better ways to build a kernel that integrates really nicely into a debian based system.  In the past I have used this guide and it's worked well: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by sergioperr on 2008-07-14
The same problem:
"...
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
.../

All worked fine (makeconfig, make clean) until "make-kpkg --append...". 
I've tried all methods described in several forums, but none worked.
Only "makerproper" did a no-error result, but unusable with the ubuntu standard method.
I'm trying to install an ethernet driver from Marvell in a Toshiba laptop.

Any suggest ?
Thanks in advance !

---

### Post by ET! on 2008-07-14
i have had the same error 
try using mkinitramfs -YOURKERNELVERSION IMAGE_NAME..

then you need to edit the menu.lst file to include the compiled kernel

---

### Post by sergioperr on 2008-07-14
Thank you, ET!. I'll give it a try.

---

