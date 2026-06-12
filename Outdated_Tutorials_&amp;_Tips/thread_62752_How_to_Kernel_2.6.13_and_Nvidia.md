---
title: "How to: Kernel 2.6.13 and Nvidia"
date: 2005-09-05
forum: Outdated Tutorials &amp; Tips
---

### Post by vnbuddy2002 on 2005-09-05
This guide will save people time instead of looking around the net (like myself). :) I wanted to have a fresh new optimized kernel, so I did the fresh `server base` installation. Then, I compile the latest kernel (2.6.13). Unfortunately, NVIDIA driver doesn't seem to work right even if your compilation is completed successfully. You will receive an error like "FATAL: error to insert .... no device found".

Required package(s);
kernel-package

Let begin:

1. sudo apt-get install nvidia-kernel-source kernel-package
2. sudo cd /usr/src/
3. sudo tar xzvf nvidia-*.gz
4. sudo wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.13.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.13.tar.bz2)
5. sudo tar jxvf linux-2.6.13.tar.bz2
6. sudo ln -sf /usr/src/linux-2.6.13 /usr/src/linux
7. cd /usr/src/linux
8. sudo make menuconfig

** :) You should strip off all the unnecessary features/drivers

9. sudo make-kpkg clean
10. sudo make-kpkg --initrd kernel-image modules-image
11. cd ..
12. sudo dpkg -i kernel-image*.deb
13. sudo wget [http://download.nvidia.com/XFree86/Linux-x86/1.0-7174/NVIDIA-Linux-x86-1.0-7174-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-7174/NVIDIA-Linux-x86-1.0-7174-pkg1.run)
14. sudo sh NVIDIA-Linux-x86-1.0-7174-pkg1.run

That should be it. You should have a new kernel with nvidia driver enabled. If I miss anything, don't forget to let me know.


** Edit **
Correct some typos. :) thanks for point them out.

---

### Post by duminas on 2005-09-05
Soooooooooooooooooooo what's **nvidia-kernel**?
I try to install it, and yet I have this as output:
```
Package nvidia-kernel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-kernel has no installation candidate
```Which is rather fun. I have repositories opened up, as well as backports.

Otherwise looks good.

---

### Post by alinux on 2005-09-05
> **vnbuddy2002]This guide will save people time instead of looking around the net (like myself). :) I wanted to have a fresh new optimized kernel, so I did the fresh `server base` installation. Then, I compile the latest kernel (2.6.13). Unfortunately, NVIDIA driver doesn't seem to work right even if your compilation is completed successfully. You will receive an error like "FATAL: error to insert .... no device found".

Required package(s) said:**
> http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.13.tar.bz2[/url]
5. sudo tar jxvf linux-2.6.13.tar.bz2
6. sudo ln -sf /usr/src/linux /usr/src/linux-2.6.13
7. cd /usr/src/linux
8. sudo make menuconfig

** :) You should strip off all the unnecessary features/drivers

9. sudo make-kpkg clean
10. sudo make-kpkg --initrd kernel-image modules-image
11. cd ..
12. sudo dpkg -i kernel-image*.deb
13. sudo wget [http://download.nvidia.com/XFree86/Linux-x86/1.0-7174/NVIDIA-Linux-x86-1.0-7174-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-7174/NVIDIA-Linux-x86-1.0-7174-pkg1.run)
14. sudo sh NVIDIA-Linux-x86-1.0-7174-pkg1.run

That should be it. You should have a new kernel with nvidia driver enabled. If I miss anything, don't forget to let me know.
 ln -sf /usr/src/linux-2.6.13 /usr/src/linux

correction :)

---

### Post by vnbuddy2002 on 2005-09-05
Sorry, it should be "nvidia-kernel-source"

---

