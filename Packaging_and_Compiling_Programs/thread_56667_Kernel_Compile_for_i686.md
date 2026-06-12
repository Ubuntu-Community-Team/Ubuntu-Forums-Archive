---
title: "Kernel Compile for i686"
date: 2005-08-13
forum: Packaging and Compiling Programs
---

### Post by kommissar on 2005-08-13
Hello everyone.  I am currently following this excellent guide on how to compile your own kernel found here: [https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

Everything is working well for me, but I have one question.  When the make-kpkg is complete it produces a deb with an _i386 in the file name.  However, I run a pentium 4 and would like the compiler to optimize for the i686 architecture.  Is there a config file that I have to edit somewhere or flags that I have to set for GCC?  I'm used to gentoo's /etc/make.conf so in Ubuntu I'm not sure where to look.  Thanks for your help!

---

### Post by PeP on 2005-08-13
it is one of the options you set up in make menuconfig (or whatever make <foo>config you use)
in processor type and features -> processor family

---

### Post by kommissar on 2005-08-13
[QUOTE=PeP]it is one of the options you set up in make menuconfig (or whatever make <foo>config you use)
in processor type and features -> processor family[/QUOTE]
I have it on Pentium 4, maybe it's just giving it a strange i386 label for some reason.  It comes out like this: kernel-image-2.6.11.08132005_10.00.Custom_i386.deb (the 08132005 is my custom date label).

---

