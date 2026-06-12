---
title: "Broken Packages Will Not Fix"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by cbennett926 on 2013-06-06
Hello all,

I have tried and tried all day (past 8 hours) on trying to fix my broken packages. Basically, I was trying to remove old kernels and now I get crazy package errors. I tried to update using software updater and it says I have broken packages and to use synaptic, well then I get an error that it didn't work on fixing the broken packages so I try install -f.


Here's what happens 

```
 
cody@cody-ThinkPad-W520:~$ sudo apt-get install -f
[sudo] password for cody: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-27-generic linux-image-3.8.0-19-generic
  linux-image-extra-3.5.0-27-generic linux-image-extra-3.8.0-19-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 317 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 261036 files and directories currently installed.)
Removing linux-image-extra-3.5.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-23-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.5.0-27-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.5.0-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.5.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-23-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.5.0-27-generic.postrm line 328.
dpkg: error processing linux-image-3.5.0-27-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-23-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-extra-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.8.0-23-generic...
P: Writing config for /boot/vmlinuz-3.8.0-21-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.8.0-19-generic.postrm line 328.
dpkg: error processing linux-image-3.8.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.5.0-27-generic
 linux-image-3.5.0-27-generic
 linux-image-extra-3.8.0-19-generic
 linux-image-3.8.0-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
cody@cody-ThinkPad-W520:~$ 


```

If I run apt-get update it all goes smooth with no errors though.. 

Any help?

---

### Post by cbennett926 on 2013-06-06
Never have I been more frustrated in the simple mistakes we make... 


I had an extra quote in my grub file and as such nothing would work. I removed the quote, re ran upgrade and everything, all fixed!

So moral of the story folks, mind your grammar...

---

