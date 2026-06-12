---
title: "Libc6 Package not installing - Help"
date: 2018-01-29
forum: Packaging and Compiling Programs
---

### Post by gounden123 on 2018-01-29
```
sudo apt-get install libc6:i386
[sudo] password for zeus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6:i386 is already the newest version (2.23-0ubuntu10).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-4.4.0-112-generic (4.4.0-112.135) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-112-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-112-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-112-generic:
 linux-image-extra-4.4.0-112-generic depends on linux-image-4.4.0-112-generic; however:
  Package linux-image-4.4.0-112-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-112-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-112-generic; however:
  Package linux-image-4.4.0-112-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-112-generic; however:
  Package linux-image-extra-4.4.0-112-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.112.118); however:
  Package linux-image-generic is not No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                 No apport report written because the error message indicates it's a follow-up error from a previous failure.
             No apport report written because MaxReports has already been reached
 configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.13.0-32-generic (4.13.0-32.35~16.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.13.0-32-generic.postinst line 1052.
dpkg: error processing package linux-image-4.13.0-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-image-extra-4.13.0-32-generic:
 linux-image-extra-4.13.0-32-generic depends on linux-image-4.13.0-32-generic; however:
  Package linux-image-4.13.0-32-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.13.0-32-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-image-generic-hwe-16.04:
 linux-image-generic-hwe-16.04 depends on linux-image-4.13.0-32-generic; however:
  Package linux-image-4.13.0-32-generic is not configured yet.
 linux-image-generic-hwe-16.04 depends on linux-image-extra-4.13.0-32-generic; however:
  Package linux-image-extra-4.13.0-32-generic is not configured yet.

dpkg: error processing package linux-image-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.13.0.32.52); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.

dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-4.4.0-112-generic
 linux-image-extra-4.4.0-112-generic
 linux-image-generic
 linux-generic
 linux-image-4.13.0-32-generic
 linux-image-extra-4.13.0-32-generic
 linux-image-generic-hwe-16.04
 linux-generic-hwe-16.04
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wildmanne39 on 2018-01-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by &amp;KyT$0P# on 2018-01-29
Please post the output from running this command in Terminal -
```
cat /etc/default/grub
```

---

