---
title: "NDiswrapper Build (?) Crash"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by Tuxedo Mask on 2013-06-14
Hi all,

A while ago, I sought to build ndiswrapper version 1.57 for some reason or other (I can't even remember why now). It didn't work out too well, either because of a kernel conflict or me just missing a step as I tend to do. Anyways, every so often, after using an upgrade manager I'll get a crash report from ndiswrapper saying that it's kernel module failed to build. Here's the crash report from /var/crash:

```

ProblemType: Package
DKMSBuildLog:
 DKMS make.log for ndiswrapper-1.57 for kernel 3.5.0-34-generic (i686)
 Fri Jun 14 10:55:09 EDT 2013
 make -C /usr/src/linux-headers-3.5.0-34-generic M=/var/lib/dkms/ndiswrapper/1.57/build
 make[1]: Entering directory `/usr/src/linux-headers-3.5.0-34-generic'
   LD      /var/lib/dkms/ndiswrapper/1.57/build/built-in.o
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/crt_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/hal_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ndis_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_io_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/rtl_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/usb_exports.h
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/crt.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/hal.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/iw_ndis.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/loader.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/ndis.o
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
 make[2]: *** [/var/lib/dkms/ndiswrapper/1.57/build/ndis.o] Error 1
 make[1]: *** [_module_/var/lib/dkms/ndiswrapper/1.57/build] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-34-generic'
 make: *** [modules] Error 2
DKMSKernelVersion: 3.5.0-34-generic
Date: Fri Jun 14 10:55:19 2013
DuplicateSignature:
 DKMS make.log for ndiswrapper-1.57 for kernel 3.5.0-34-generic (i686)
 make -C /usr/src/linux-headers-3.5.0-34-generic M=/var/lib/dkms/ndiswrapper/1.57/build
 make[1]: Entering directory `/usr/src/linux-headers-3.5.0-34-generic'
   LD      /var/lib/dkms/ndiswrapper/1.57/build/built-in.o
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/crt_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/hal_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ndis_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/ntoskernel_io_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/rtl_exports.h
   MKEXPORT /var/lib/dkms/ndiswrapper/1.57/build/usb_exports.h
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/crt.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/hal.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/iw_ndis.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/loader.o
   CC [M]  /var/lib/dkms/ndiswrapper/1.57/build/ndis.o
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c: In function ‘NdisGetCurrentProcessorCounts’:
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2657:24: error: ‘struct kernel_stat’ has no member named ‘cpustat’
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2658:31: error: ‘struct kernel_stat’ has no member named ‘cpustat’
 /var/lib/dkms/ndiswrapper/1.57/build/ndis.c:2659:17: error: ‘struct kernel_stat’ has no member named ‘cpustat’
 make[2]: *** [/var/lib/dkms/ndiswrapper/1.57/build/ndis.o] Error 1
 make[1]: *** [_module_/var/lib/dkms/ndiswrapper/1.57/build] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-34-generic'
 make: *** [modules] Error 2
 
Package: ndiswrapper-dkms
PackageVersion: 1.57-1ubuntu1
SourcePackage: ndiswrapper
Title: ndiswrapper-dkms 1.57-1ubuntu1: ndiswrapper kernel module failed to build
ApportVersion: 2.0.1-0ubuntu17.3
Architecture: i386
Dependencies:
 binutils 2.22-6ubuntu1
 coreutils 8.13-3ubuntu3.2
 cpp 4:4.6.3-1ubuntu5
 cpp-4.6 4.6.3-1ubuntu5
 debconf 1.5.42ubuntu1
 dkms 2.2.0.3-1ubuntu3.1
 dpkg 1.16.1.2ubuntu7.1
 gcc 4:4.6.3-1ubuntu5
 gcc-4.6 4.6.3-1ubuntu5
 gcc-4.6-base 4.6.3-1ubuntu5
 libacl1 2.2.51-5ubuntu1
 libattr1 1:2.4.46-5ubuntu1
 libbz2-1.0 1.0.6-1
 libc-bin 2.15-0ubuntu10.4
 libc6 2.15-0ubuntu10.4
 libgcc1 1:4.6.3-1ubuntu5
 libgmp10 2:5.0.2+dfsg-2ubuntu1
 libgomp1 4.6.3-1ubuntu5
 liblzma5 5.1.1alpha+20110809-3
 libmpc2 0.9-4
 libmpfr4 3.1.0-3ubuntu2
 libquadmath0 4.6.3-1ubuntu5
 libselinux1 2.1.0-4.1ubuntu1
 libstdc++6 4.6.3-1ubuntu5
 make 3.81-8.1ubuntu1.1
 module-init-tools 3.16-1ubuntu2
 multiarch-support 2.15-0ubuntu10.4
 patch 2.6.1-3
 perl-base 5.14.2-6ubuntu2.3
 tar 1.26-4ubuntu1
 tzdata 2012e-0ubuntu0.12.04.1
 xz-utils 5.1.1alpha+20110809-3
 zlib1g 1:1.2.3.4.dfsg-3ubuntu4
DistroRelease: Ubuntu 12.04
InstallationMedia: Ubuntu 12.04 LTS "Precise Pangolin" - Release i386 (20120423)
MarkForUpload: True
PackageArchitecture: all
ProcVersionSignature: Ubuntu 3.5.0-32.53~precise1-generic 3.5.7.11
Tags:  precise
Uname: Linux 3.5.0-32-generic i686
UpgradeStatus: No upgrade log present (probably fresh install)

```

As you can see, I'm running 3.5.0-32 generic (it's set to go to 34 when I restart, though; they just downloaded right before the crash report). I'd like to wipe my hands of this mess and just get rid of all this ndiswrapper stuff altogether, but I'm not sure where to start.

Thanks.

---

### Post by Kopkins on 2013-06-14
Do you use ndiswrapper?

Which wireless card do you have?

Kopkins

---

### Post by Tuxedo Mask on 2013-06-14
I don't believe it's engaged at the moment; now that I think about it, I think I installed it to control this Netgear WG111v2 USB dongle. I guess I could give it another shot, in which case I suppose I'd need to repair the install somehow?

---

