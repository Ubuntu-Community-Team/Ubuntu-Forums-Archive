---
title: "software centre broke"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by thetrooper on 2013-03-30
Software centre is telling me it is broken ,given chanec to but refuses to repair any ideas please and get a message at the same time to run apt-get install -f  tin the terminal  get
 (trooper1a@trooper1a-HP-625:~$ sudo apt-get install -f
[sudo] password for trooper1a: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-image-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/4,310 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-38-generic (3.2.0-38.61) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic
W: TMPDIR is mounted noexec, will not cache run scripts.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic /boot/vmlinuz-3.2.0-38-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash”: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-39-generic (3.2.0-39.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic
W: TMPDIR is mounted noexec, will not cache run scripts.
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash”: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.9) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash”: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-38-generic; however:
  Package linux-image-3.2.0-38-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.38.46); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-headers-generic (= 3.2.0.38.46); however:
  Version of linux-headers-generic on system is 3.2.0.39.47.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        Errors were encountered while processing:
 linux-image-3.2.0-38-generic
 linux-image-3.2.0-39-generic
 grub-pc
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
trooper1a@trooper1a-HP-625:~$ 
/var/lib/dpkg/), are you root?
trooper1a@trooper1a-HP-625:~$ 

Thanks

---

### Post by fantab on 2013-03-30
That suggests that you have a bad upgrade or some other issue with "linux-image-3.2.0-38-generic" and "linux-image-3.2.0-39-generic". We will have to remove them. But first we have to ensure that we are not using the said kernel-images:

```
$ uname -r
```

The output from the above command will tell you what kernel version you are using. If you are not using the ones in question then:


```
$ sudo apt-get remove --purge linux-image-3.2.0-38-generic linux-image-3.2.0-39-generic 
$ sudo apt-get clean  
$ sudo apt-get install -f  
$ sudo dpkg --configure -a 
$ sudo apt-get update
```

By the way, if you "Synaptic Package Manager" installed you can use it to do the same from the comfort of GUI.

---

