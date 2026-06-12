---
title: "initramfs-tools stuck in loop"
date: 2010-05-18
forum: Repositories &amp; Backports
---

### Post by JHSPerc on 2010-05-18
Tried several of the fixes listed here, on bugs site, and around the interweb and none are working.... 

> root@ubuntu:/lib/udev# cd udev-firmware.patch
bash: cd: udev-firmware.patch: Not a directory
root@ubuntu:/lib/udev# sudo dpkg --configure -aSetting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
Removing old bcmwl-5.60.48.36+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.60.48.36+bdcom
Kernel:  2.6.32-21-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-21-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.60.48.36+bdcom
Kernel:  2.6.32-22-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-22-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.60.48.36+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.60.48.36+bdcom DKMS files...
First Installation: checking all kernels...
Building for 2.6.32-21-generic and 2.6.32-22-generic
Building for architecture i686
Building initial module for 2.6.32-21-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-21-generic/updates/dkms/

depmod....

DKMS: install Completed.
Building initial module for 2.6.32-22-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
cp: cannot stat `/vmlinuz': No such file or directory
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-2.6.32-22-generic:
 linux-image-2.6.32-22-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 bcmwl-kernel-source
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic


I am new to linux so if you need me to post files or run something, please be specific. I really want to clear this up as its really irritating me.

---

### Post by jards on 2010-06-24
I'm having the same problem, and don't know what to do.

I'm using a USB of ubuntu lucid in a Dell Vostro 1320, trying to fix a wireless problem, and other functions, and everything I start to do in Terminal stops on this.

Thanks.

---

