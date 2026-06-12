---
title: "Fresh install of 8.10 GRUB problem"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by jmtjet on 2008-11-08
I have three hard drives installed in this computer. I use a Trios selector switch(no longer made)to select which drive to boot to. Drive one has Windows 2K pro. on it, drive two is the one I'm trying to install to and drive three has Ubuntu 8.04 installed and running well. I know what the problem is, just don't know how to correct it. On booting number two drive I see that it is listed as "slave" on the boot screen. I don't think I can change that due to the Trios switch so I want to know if I can direct GRUB to the slave drive? After the install of Ubuntu 8.10 to number two drive I get GRUB error 2 on reboot. Any advice with this? 

Note: I had Linux Mint installed and working on the drive in question prior to the 8.10 install. Thanks.

---

### Post by Crafty Kisses on 2008-11-08
Can you post the results of these commands?
```
cat /boot/grub/menu.lst
sudo fdisk -l
```
This will tell me a few things.

---

### Post by jmtjet on 2008-11-08
The first command did not work. Got the message"no such file" or something like that. The second command did work I'm post the output below. I'm running from the "live" CD to get this.

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 46.1 GB, 46103371776 bytes
255 heads, 63 sectors/track, 5605 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001705b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5370    43134493+  83  Linux
/dev/sda2            5371        5605     1887637+   5  Extended
/dev/sda5            5371        5605     1887606   82  Linux swap / Solaris

Disk /dev/sdc: 256 MB, 256900608 bytes
16 heads, 32 sectors/track, 979 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x8a379214

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979      250574+   6  FAT16

Looks to me like GRUB is trying to boot from a 256MB USB flash drive?

---

### Post by caljohnsmith on 2008-11-09
So when you use your Trios selector, does it make the other drives invisible to BIOS, i.e. as though they are disconnected? I'm asking because your fdisk output only shows two drives, your linux drive and a small 256 MB drive (maybe a flash drive?). 

How about doing this from your Live CD to install Grub to the MBR of the linux sda drive:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Please post the output of all the above commands. Also, I notice that none of your partitions on the sda drive are marked as bootable, and some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable; since you are getting a Grub error on start up, most likely this is not an issue, but it could only help and not hurt to mark one of your partitions as bootable just in case it has anything to do with your problem. So from the Live CD:
```
sudo fdisk /dev/sda
```
Type "a" to toggle the boot flag, "1" for the partition, "w" to write the change, and then "q" to quit fdisk. After that, reboot your computer, make sure you have the linux drive set to boot, and let me know what happens. We can work from there. :)

---

### Post by jmtjet on 2008-11-09
Thanks for your help. The first set of commands gave me the following:
grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found


 I've completed the second set of commands and will reboot. But since this is a new install I'm wondering if I made a wrong selection during the install that's causing this problem? I'll get back to you after the reboot.

---

### Post by jmtjet on 2008-11-09
After the reboot I got the same error as before: GRUB error 2.

---

