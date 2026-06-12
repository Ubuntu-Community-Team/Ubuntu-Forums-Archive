---
title: "Linux source\headers needed for compiling"
date: 2009-09-23
forum: Packaging and Compiling Programs
---

### Post by Corsair Freak on 2009-09-23
Hi all,

I'm new to the Linux scene and have only been using some various Linux distributions for the past two weeks. But, in those two weeks I think I've installed ubuntu/kubuntu/xubuntu and fedora about a dozen times. Currently, I'm running a minimal install of kubuntu using the mini.iso. So far the only snag I've run into that trial-and-error won't fix is compiling the NVIDIA and RealTek drivers. I get an error whenever I try to compile either of those and both error messages are fairly similar. The error message tells me I need to install the Linux kernel source (or maybe headers?). I've tried "build-essential" but that didn't cure my problem. I've also downloaded the source for the 2.6.28-15 Linux kernel in the ubuntu package database to no avail. Can anyone please point me in the right direction of which packages I need to successfully compile from source?

Currently, the only packages and required dependencies I have installed are:

xorg
kde-core
kdm
kdebase
kpackagekit
ark
Firefox (via ubuntuzilla)

Any and all help is appreciated,
Corsair Freak

P.S. My PC architecture is 32-bit, the partition format for kubuntu is ext4, and my kernel version is 2.6.28-15-gerneric.

---

### Post by yabbadabbadont on 2009-09-23
Assuming that you are using the default, linux-generic, kernel, then you just need to:
```
sudo apt-get install linux-headers-generic
```

---

### Post by Corsair Freak on 2009-09-24
Thanks! That worked for the NVIDIA driver, it's installed and working now. But I'm getting a new error with RealTek HD Audio driver I'm trying to install. I won't paste the entire output because it's fairly long but this at the top is fairly interesting:

> checking for kernel version... 2.6.28-15-generic                                                    
checking for GCC version... ./configure: eval: line 5233: syntax error near unexpected token `)'    
./configure: eval: line 5233: `my_compiler_version=4.3.3-5ubuntu4)'                                 
Kernel compiler:  Used compiler: gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3                                  

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.Then at the end after it gets done checking for a few hundred files it says: > ./configure: line 9298: syntax error: unexpected end of fileI've installed this driver on the default installs of k/x/ubuntu with no problem. I'm sure I'm just missing a package or a compiler but I haven't got a clue. Without the driver installed I have to turn my speakers up ALL the way for the sounds to be heard clearly.

Currently installed packages:
xorg
kde-core
kdm
kdebase
kpackagekit
ark
Firefox [using ubuntuzilla]
kopete
linux-headers-generic
build-essential
kubuntu-restricted-extras
amarok
kmix

Thanks for your help,
Corsair Freak

---

### Post by Corsair Freak on 2009-09-26
I started over again with my Kubuntu minimal install and for some reason the RealTek driver decided to compile this time, even though I didn't do anything different. Go figure.

---

