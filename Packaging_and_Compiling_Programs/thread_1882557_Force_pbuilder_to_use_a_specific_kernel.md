---
title: "Force pbuilder to use a specific kernel?"
date: 2011-11-17
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-11-17
How might I force pbuilder to use a specific kernel? 

I'm trying to use pbuilder to compile a .ko module for 2.6. My host machine is using 3.0 (Xubuntu 11.10); the target machines will use 2.6 (Server 10.04.3). 

pbuilder-dist returns a 3.0 kernel for "uname -r". I can get around some of the issues this obviously causes by hard-coding the kernel version I want into the Makefile. However, I cannot test the .ko in pbuilder since it's using a 3.0 kernel. How might I switch kernels?

---

### Post by Bachstelze on 2011-11-17
You need at least a virtual machine like qemu or VirtualBox. You can't run a different kernel in pbuilder, it's basically just a chroot.

---

### Post by djsephiroth on 2011-11-17
Thanks; that answers my question.

---

