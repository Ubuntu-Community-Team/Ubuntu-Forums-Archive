---
title: "Error Message:  Package linux-image-generic-pae is not configured yet"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by anubyss on 2012-10-25
Hello all, another person new to the Linux world.  I am running Ubuntu 12.04 from a USB stick and initially wanted to see if ddrescue could recover some data from a failed drive.  I don't know much basically as I've been reading up for only a few days specifically on data recovery using Linux. 

Here is the list of drives with sdc being the usb drive that was created using Universal USB Installer (if that matters). 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
/dev/sda2   *      208845   312576704   156183930    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e9ea3e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3906983998  1953491968    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          44    15679439     7839698    c  W95 FAT32 (LBA)

I am assuming this message is for some type of encryption?
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab

I am not sure what to make of the "linux-image-3.2.0-32-generic-pae" message.

Entire result of sudo apt-get autoremove
ubuntu@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-32-generic-pae (3.2.0-32.51) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-32-generic-pae /boot/vmlinuz-3.2.0-32-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-32-generic-pae
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-32-generic-pae /boot/vmlinuz-3.2.0-32-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-32-generic-pae /boot/vmlinuz-3.2.0-32-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-32-generic-pae /boot/vmlinuz-3.2.0-32-generic-pae
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-32-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-32-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-32-generic-pae; however:
  Package linux-image-3.2.0-32-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.32.35); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                    Errors were encountered while processing:
 linux-image-3.2.0-32-generic-pae
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks all.

---

### Post by Bashing-om on 2012-10-25
Hi ! anubyss; Welcome back to the forum;

If I may propose, reinstall ubuntu to the usb device. This time insure the partitions are not encrypted. These links may prove helpful:
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I am not familiar with usb installs, however the format on sdc may be invalid.  ubuntu's file format is ext4 -your fdisk output shows the device formated as fat32 ???
I would expect the installer to automagically format the usb device to ext4 ? So can not advise in this regard ..as the installer should do the formating[ if you are formating before hand for installing ...don't .
[INDENT]best regards, any questions, post back <== BDQ

[/INDENT]

---

### Post by anubyss on 2012-10-26
I just recreated a usb drive and everything was fine.  But as soon as run 'updates available', I get error messages.  So I am guessing one of the updates is creating an issue.  I've recreated a usb drive and now am installing software I am going to use without issues.  Thanks for the help.

---

### Post by Bashing-om on 2012-10-26
You are most welcome.....we are all in this together !

As content -> please mark thread as solved....tks

[INDENT]happy ubuntu'n <==BDQ

[/INDENT]

---

