---
title: "Compiling my first kernel"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Yoruichi on 2008-09-22
after i compile the correct modules i get this error which appears to be an input i need a crash course on this also it say something abot fakeroot

> ONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic

---

### Post by Crafty Kisses on 2008-09-22
To start, you will need to install a few packages.
```
sudo apt-get install linux-kernel-devel fakeroot build-essential
```
This will install the compiler related packages and kernel packaging tools. It will also install the git-core package, which is the best way to interact with the Ubuntu kernel source. It sounds like you're at the top directory of the kernel source tree, so try the following: ```
cp -vi /boot/config-`uname -r` .config
```
Before you run ```
make menuconf
``` Or ```
make xconfig
```Make sure you have the necessary packages installed before doing so. Now that you've told initramfs-tools what modules it should include and the build is complete, you can install the generated debs using dpkg:
```
sudo dpkg -i linux-image-2.6.20-16-2be-k7_2.6.20-16_i386.deb
sudo dpkg -i linux-headers-2.6.20-16-2be-k7_2.6.20-16_i386.deb
```
That should solve your issues, if you have any other problems, please let me know.

---

### Post by prshah on 2008-09-22
> **Codename said:**
> 
```
sudo apt-get install linux-kernel-devel fakeroot build-essential
```

[offtopic & hijack][indent]Thanks, I've been wondering for the longest time where to get the ubuntu kernel sources, and not kernel.org kernel sources. [/indent][/offtopic & hijack]

---

