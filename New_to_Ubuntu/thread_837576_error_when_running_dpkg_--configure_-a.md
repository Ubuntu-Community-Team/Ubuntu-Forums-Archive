---
title: "error when running dpkg --configure -a"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by friedfisherman on 2008-06-22
Setting up linux-image-2.6.24-19-generic (2.6.24-19.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-19-generic; however:
  Package linux-restricted-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.19.21); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
hawk@hawk-desktop:~$

---

### Post by oldos2er on 2008-06-22
"No space left on device" means your partition is full.

---

### Post by inportb on 2008-06-22
Indeed... see if you can uninstall some older kernels, or clear the apt archive: *sudo apt-get clean*

---

