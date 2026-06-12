---
title: "Vmware work station 7.1 ununtu 11.10 help"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by qpens on 2011-10-22
Kernel module updater fail. any solutions?
Unable to build kernel module



Oct 22 14:27:57.333: app-3078272704| Log for VMware Workstation pid=5927 version=7.1.5 build=build-491717 option=Release
Oct 22 14:27:57.333: app-3078272704| The process is 32-bit.
Oct 22 14:27:57.333: app-3078272704| Host codepage=UTF-8 encoding=UTF-8
Oct 22 14:27:57.333: app-3078272704| Logging to /tmp/vmware-root/setup-5927.log
Oct 22 14:27:57.923: app-3078272704| modconf query interface initialized
Oct 22 14:27:57.923: app-3078272704| modconf library initialized
Oct 22 14:27:58.031: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.054: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.105: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.210: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.243: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.395: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.410: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.426: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.445: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.459: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.508: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.528: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.535: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.542: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.549: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.557: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.572: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.640: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.646: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.653: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.660: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.667: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.675: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.691: app-3078272704| Your GCC version: 4.6
Oct 22 14:27:58.819: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.834: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.853: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.868: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:58.879: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:59.523: app-3078272704| Trying to find a suitable PBM set for kernel 3.0.0-13-generic.
Oct 22 14:27:59.526: app-3078272704| Building module vmmon.
Oct 22 14:27:59.527: app-3078272704| Extracting the sources of the vmmon module.
Oct 22 14:27:59.579: app-3078272704| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-13-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Oct 22 14:28:02.971: app-3078272704| Failed to compile module vmmon!

---

### Post by snovik on 2011-10-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/840472](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/840472)

---

