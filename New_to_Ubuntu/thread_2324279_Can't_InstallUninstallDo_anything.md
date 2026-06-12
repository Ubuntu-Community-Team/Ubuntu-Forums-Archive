---
title: "Can't Install/Uninstall/Do anything"
date: 2016-05-12
forum: New to Ubuntu
---

### Post by ccapmag on 2016-05-12
I am unable to install or uninstall any applications.

When I run 
```

sudo dpkg --configure -a

```
the output is:
```

dpkg: dependency problems prevent configuration of linux-signed-image-3.19.0-59-generic:
 linux-signed-image-3.19.0-59-generic depends on linux-image-3.19.0-59-generic (= 3.19.0-59.65~14.04.1); however:
  Package linux-image-3.19.0-59-generic is not installed.


dpkg: error processing package linux-signed-image-3.19.0-59-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-56-generic:
 linux-image-extra-3.19.0-56-generic depends on linux-image-3.19.0-56-generic; however:
  Package linux-image-3.19.0-56-generic is not installed.


dpkg: error processing package linux-image-extra-3.19.0-56-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
 linux-image-generic-lts-vivid depends on linux-image-3.19.0-59-generic; however:
  Package linux-image-3.19.0-59-generic is not installed.


dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.19.0-56-generic:
 linux-signed-image-3.19.0-56-generic depends on linux-image-3.19.0-56-generic (= 3.19.0-56.62~14.04.1); however:
  Package linux-image-3.19.0-56-generic is not installed.
 linux-signed-image-3.19.0-56-generic depends on linux-image-extra-3.19.0-56-generic (= 3.19.0-56.62~14.04.1); however:
  Package linux-image-extra-3.19.0-56-generic is not configured yet.


dpkg: error processing package linux-signed-image-3.19.0-56-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.19.0-47-generic (3.19.0-47.53~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-47-generic


gzip: stdout: No space left on device
E: mkinitramfs failure find 141 cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-47-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-signed-image-generic-lts-vivid:
 linux-signed-image-generic-lts-vivid depends on linux-signed-image-3.19.0-59-generic; however:
  Package linux-signed-image-3.19.0-59-generic is not configured yet.


dpkg: error processing package linux-signed-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.19.0-47-generic:
 linux-signed-image-3.19.0-47-generic depends on linux-image-extra-3.19.0-47-generic (= 3.19.0-47.53~14.04.1); however:
  Package linux-image-extra-3.19.0-47-generic is not configured yet.


dpkg: error processing package linux-signed-image-3.19.0-47-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-59-generic:
 linux-image-extra-3.19.0-59-generic depends on linux-image-3.19.0-59-generic; however:
  Package linux-image-3.19.0-59-generic is not installed.


dpkg: error processing package linux-image-extra-3.19.0-59-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-image-generic-lts-vivid (= 3.19.0.59.42); however:
  Package linux-image-generic-lts-vivid is not configured yet.


dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic-lts-vivid:
 linux-signed-generic-lts-vivid depends on linux-signed-image-generic-lts-vivid (= 3.19.0.59.42); however:
  Package linux-signed-image-generic-lts-vivid is not configured yet.


dpkg: error processing package linux-signed-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-signed-image-3.19.0-59-generic
 linux-image-extra-3.19.0-56-generic
 linux-image-generic-lts-vivid
 linux-signed-image-3.19.0-56-generic
 linux-image-extra-3.19.0-47-generic
 linux-signed-image-generic-lts-vivid
 linux-signed-image-3.19.0-47-generic
 linux-image-extra-3.19.0-59-generic
 linux-generic-lts-vivid
 linux-signed-generic-lts-vivid

```

---

### Post by ian-weisser on 2016-05-12
Please show us the complete output of the following three commands:
```
df
df -i
dpkg -l | grep linux

```

---

