---
title: "Error over installation"
date: 2019-01-31
forum: New to Ubuntu
---

### Post by matuskm on 2019-01-31
Hi,

I have a probleme with installation app.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sbackup is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
15 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-3.13.0-157-generic (3.13.0-157.207) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-164-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-157-generic /boot/vmlinuz-3.13.0-157-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-157-generic /boot/vmlinuz-3.13.0-157-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-157-generic /boot/vmlinuz-3.13.0-157-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-157-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-157-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-157-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-157-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.13.0-164-generic (3.13.0-164.214) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.13.0-157-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-164-generic /boot/vmlinuz-3.13.0-164-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-164-generic /boot/vmlinuz-3.13.0-164-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-164-generic /boot/vmlinuz-3.13.0-164-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-164-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-164-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-164-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-164-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-firmware (1.127.24) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-161-generic
grep: /boot/config-3.13.0-161-generic: No such file or directory
WARNING: missing /lib/modules/3.13.0-161-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-161-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_lK236B/lib/modules/3.13.0-161-generic/modules.order: No such file or directory
depmod:  WARNING: could not open  /tmp/mkinitramfs_lK236B/lib/modules/3.13.0-161-generic/modules.builtin:  No such file or directory
update-initramfs: Generating /boot/initrd.img-3.13.0-153-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-153-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-164-generic:
 linux-image-extra-3.13.0-164-generic depends on linux-image-3.13.0-164-generic; however:
  Package linux-image-3.13.0-164-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-164-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-164-generic; however:
  Package linux-image-3.13.0-164-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-164-generic; however:
  Package linux-image-extra-3.13.0-164-generic is not configured yet.
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generiNo apport report written because MaxReports is reached already
                                                                                                                              No apport report written because MaxReports is reached already
               No apport report written because MaxReports is reached already
                                                                             c:
 linux-generic depends on linux-image-generic (= 3.13.0.164.174); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.13.0-142-generic (3.13.0-142.191) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-142-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-142-generic /boot/vmlinuz-3.13.0-142-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-142-generic /boot/vmlinuz-3.13.0-142-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-142-generic /boot/vmlinuz-3.13.0-142-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-142-generic
grep: /boot/config-3.13.0-142-generic: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-142-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-142-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                               Setting up linux-image-extra-3.13.0-153-generic (3.13.0-153.203) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-153-generic /boot/vmlinuz-3.13.0-153-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-153-generic /boot/vmlinuz-3.13.0-153-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-153-generic /boot/vmlinuz-3.13.0-153-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-153-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-153-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
No apport report written because MaxReports is reached already
                                                               dpkg: error processing package linux-image-extra-3.13.0-153-generic  (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                             No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                             No apport report written because MaxReports is reached already
                                                                                                                                           No apport report written because MaxReports is reached already
                            No apport report written because MaxReports is reached already
                                                                                           dpkg: dependency problems prevent configuration of  linux-image-extra-3.13.0-157-generic:
 linux-image-extra-3.13.0-157-generic depends on linux-image-3.13.0-157-generic; however:
  Package linux-image-3.13.0-157-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-157-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-164-generic:
 linux-signed-image-3.13.0-164-generic depends on linux-image-3.13.0-164-generic (= 3.13.0-164.214); however:
  Package linux-image-3.13.0-164-generic is not configured yet.
 linux-signed-image-3.13.0-164-generic depends on linux-image-extra-3.13.0-164-generic (= 3.13.0-164.214); however:
  Package linux-image-extra-3.13.0-164-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.13.0-164-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-3.13.0-164-generic; however:
  Package linux-signed-image-3.13.0-164-generic is not configured yet.
 linux-signed-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 3.13.0.164.174); however:
  Package linux-signed-image-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-142-generic:
 linux-signed-image-3.13.0-142-generic depends on linux-image-extra-3.13.0-142-generic (= 3.13.0-142.191); however:
  Package linux-image-extra-3.13.0-142-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.13.0-142-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-153-generic:
 linux-signed-image-3.13.0-153-generic depends on linux-image-extra-3.13.0-153-generic (= 3.13.0-153.203); however:
  Package linux-image-extra-3.13.0-153-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.13.0-153-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-3.13.0-157-generic:
 linux-signed-image-3.13.0-157-generic depends on linux-image-3.13.0-157-generic (= 3.13.0-157.207); however:
  Package linux-image-3.13.0-157-generic is not configured yet.
 linux-signed-image-3.13.0-157-generic depends on linux-image-extra-3.13.0-157-generic (= 3.13.0-157.207); however:
  Package linux-image-extra-3.13.0-157-generic is not configured yet.

dpkg: error processing package linux-signed-image-3.13.0-157-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.13.0-157-generic
 linux-image-3.13.0-164-generic
 linux-firmware
 linux-image-extra-3.13.0-164-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.13.0-142-generic
 linux-image-extra-3.13.0-153-generic
 linux-image-extra-3.13.0-157-generic
 linux-signed-image-3.13.0-164-generic
 linux-signed-image-generic
 linux-signed-generic
 linux-signed-image-3.13.0-142-generic
 linux-signed-image-3.13.0-153-generic
 linux-signed-image-3.13.0-157-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Install the app okay but during installation display errors.

Thanks

---

### Post by SeijiSensei on 2019-01-31
You have way too many stale kernels and thus are probably running out of space in /boot.

Usually Ubuntu will keep just the previous and new kernels. Sometimes that procedure can awry though.  I'd start by removing the oldest kernels and associated files:

```

sudo apt remove linux-image-3.13.0-142-generic
sudo apt remove linux-image-3.13.0-153-generic

```

---

