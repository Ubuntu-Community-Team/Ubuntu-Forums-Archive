---
title: "apt-get error"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by gimmejimmy on 2008-10-31
Hello, whenever I use apt-get to install or upgrade I get the following error:

> dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Things install just fine except for the error.  I've browsed around the forum and Google results with no luck.

---

### Post by CJ Master on 2008-10-31
Hey, It could just be that the servers are swamped because of ibex.

Try this:
1) Go to System -> Administration -> Software sources
2) Click the dialog that says something like "Server for xxx" (xxx being your country) or "Main Server", and choose other. Try another one.

Try that a few times, and see if that helps any.

---

### Post by aramadia on 2008-10-31
or **sudo apt-get clean** ?

---

### Post by gimmejimmy on 2008-10-31
I tried both suggestions, but the error persists.  If it helps any, before it starts the upgrade (apt-get upgrade) it says

> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y


Could it have something to do with the "1 not fully installed or removed" part?

---

### Post by CJ Master on 2008-10-31
That really sounds like a problem of your servers being swamped. I would try just a few more servers.

---

### Post by cariboo on 2008-10-31
I would suggest going to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages this should repair the broken kernel update.

Jim

---

### Post by gimmejimmy on 2008-10-31
Thanks for the suggestions.  Here's what I've tried so far:
1.  Changed servers:  I've tried four, including the Philippine server.  That shouldn't have heavy traffic considering Linux usage here is very low.
2.  apt-get clean
3.  Fix broken packages
4.  I also tried the suggestion here: [http://ubuntuforums.org/showthread.php?t=908541]("http://ubuntuforums.org/showthread.php?t=908541") about editing /sbin/update-grub

---

### Post by hyper_ch on 2008-10-31
try to reboot with an older kernel and then run the commands.

---

### Post by gimmejimmy on 2008-10-31
Ok, I've booted with an older kernel.  Which commands should I run?  Is there a risk of breaking anything?

---

### Post by hyper_ch on 2008-10-31
```

sudo apt-get update

```

---

### Post by gimmejimmy on 2008-10-31
Still no luck.

---

### Post by unutbu on 2008-10-31
Could you post more of the error output please?
That might give us a clue as to what is causing the error in the post-installation script.

---

### Post by gimmejimmy on 2008-10-31
Here is the output of sudo apt-get upgrade, thanks:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-21-generic (2.6.24-21.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-21.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-21.42 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.24-21-generic (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 linux-image-2.6.24-21-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by unutbu on 2008-10-31
What is the output if you type
```
sudo update-grub
```

---

### Post by gimmejimmy on 2008-10-31
It is
> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin


---

### Post by unutbu on 2008-10-31
Hm. I'm not sure what is causing update-grub to exit with value 10.

According to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235638](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/235638)
it might be caused by a full /boot partition.

I'm just fishing to find the problem here, but you might want to post the output of
```

df
sudo fdisk -l
ls -l /boot
ls -l /boot/grub
```

---

### Post by qrwe on 2008-10-31
I've got some trouble after trying the new "Create a new startup disk" feature. After running an Update, I got these similar kernel update failures:

> Setting up linux-image-2.6.27-7-generic (2.6.27-7.15) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.27-7-generic to initrd.img.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by qrwe on 2008-10-31
I've got some trouble after trying the new "Create a new startup disk" feature. After running an Update, I got these similar kernel update failures:

> Setting up linux-image-2.6.27-7-generic (2.6.27-7.15) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.27-7-generic to initrd.img.
dpkg: error processing linux-image-2.6.27-7-generic (--configure):
 subprocess post-installation script returned error exit status 17
Errors were encountered while processing:
 linux-image-2.6.27-7-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by gimmejimmy on 2008-11-01
The result of df is:
> Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             38410952   4256804  32218320  12% /
varrun                  192252       216    192036   1% /var/run
varlock                 192252         0    192252   0% /var/lock
udev                    192252        48    192204   1% /dev
devshm                  192252         0    192252   0% /dev/shm
lrm                     192252     39780    152472  21% /lib/modules/2.6.24-21-generic/volatile


fdisk -l:
> Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f3a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4820    38716618+  83  Linux
/dev/sda2            4821        4865      361462+   5  Extended
/dev/sda5            4821        4865      361431   82  Linux swap / Solaris


ls -l /boot:

> total 36292
-rw-r--r-- 1 root root  422667 2008-08-21 12:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422838 2008-10-22 11:12 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   80049 2008-08-21 12:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80062 2008-10-22 11:12 config-2.6.24-21-generic
drwxr-xr-x 2 root root    4096 2008-10-15 10:02 grub
-rw-r--r-- 1 root root 7595138 2008-09-26 09:19 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7495195 2008-09-25 03:26 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7595829 2008-11-01 23:24 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7595860 2008-10-31 23:55 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 18:06 memtest86+.bin
-rw-r--r-- 1 root root  905170 2008-08-21 12:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905617 2008-10-22 11:12 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1921464 2008-08-21 12:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920760 2008-10-22 11:12 vmlinuz-2.6.24-21-generic

ls -l /boot/grub

> total 204
-rw-r--r-- 1 root root    197 2008-09-25 01:03 default
-rw-r--r-- 1 root root     15 2008-09-25 01:03 device.map
-rw-r--r-- 1 root root   8056 2008-09-25 01:03 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-09-25 01:03 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-09-25 01:03 installed-version
-rw-r--r-- 1 root root   8608 2008-09-25 01:03 jfs_stage1_5
-rw-r--r-- 1 root root   4703 2008-10-15 10:02 menu.lst
-rw-r--r-- 1 root root   4703 2008-11-01 23:24 menu.lst~
-rw-r--r-- 1 root root   7324 2008-09-25 01:03 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-09-25 01:03 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2008-09-25 01:03 stage1
-rw-r--r-- 1 root root 108356 2008-09-25 01:03 stage2
-rw-r--r-- 1 root root   9276 2008-09-25 01:03 xfs_stage1_5

---

### Post by CJ Master on 2008-11-01
Try getting into recovery mode from the grub menu, and fixing the packages/repairing the system files from there.

---

### Post by gimmejimmy on 2008-11-02
I booted into recovery mode and tried "repair packages".  It gave the same error.  I didn't try going into the command line as root.

---

### Post by unutbu on 2008-11-02
What happens if you try uninstalling linux-image-2.6.24-21-generic and then reinstalling the same?```


sudo apt-get purge linux-image-2.6.24-21-generic
sudo apt-get install linux-image-2.6.24-21-generic
```

---

### Post by gimmejimmy on 2008-11-07
Should I do that while booted into a different kernel version?

---

