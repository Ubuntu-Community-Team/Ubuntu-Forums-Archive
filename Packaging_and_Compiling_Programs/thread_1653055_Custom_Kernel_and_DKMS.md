---
title: "Custom Kernel and DKMS"
date: 2010-12-26
forum: Packaging and Compiling Programs
---

### Post by iskarion on 2010-12-26
Hi,

I'm running Kubuntu 10.04 with a custom kernel (currently 2.6.36.2) for various reasons.

Basically I'm following these guidelines (including the Ubuntu specific packaging scripts):
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

Everything working fine so far, though one thing is always a bit puzzling.

Whenever I build and install a new kernel version, the corresponding symlink at "/lib/modules/<new kernel version/build" is automatically set to point to the kernel source in my home directory.

This of course results in DKMS failing to successfully build any modules, as some files like /include/version.h, which are dynamically generated during kernel build process, are missing in the kernel source. these files only exist in the headers at /usr/src/<new kernel version>

So I always have to change this symlink manually to /usr/src/<new kernel version> in order to get DKMS working.

This is not a big problem, but I'd like to understand how this is usually supposed to be handled on kernel installation. After all when installing a kernel from the Ubuntu repositories this symlink is also set correctly to the proper headers in /usr/src/ and no manual correction is required.

Is any special setting during kernel build (packaging scripts?) required in order get this symlink set automatically in the correct way?

---

