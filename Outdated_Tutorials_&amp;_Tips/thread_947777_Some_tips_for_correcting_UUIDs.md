---
title: "Some tips for correcting UUIDs"
date: 2008-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Patb on 2008-10-14
The purpose of this post is to explain concisely the steps to work out the correct correlation of UUIDs and device names for the Ubuntu boot process. 

For our purposes here, a [**[COLOR="Sienna"]UUID[/COLOR]**]("http://en.wikipedia.org/wiki/Universally_Unique_Identifier") is a rather long identifier for a disk partition. Every disk partition has its own unique UUID. In Ubuntu, the UUID for partitions must be correctly specified in two files: /boot/grub/menu.lst and /etc/fstab. Sometimes errors occur during boot up eg after partition changes or formatting cause changes to the UUID. Correction is often simply a matter of editing files to reflect the correct UUID designations. 

**[COLOR="Sienna"]First... [/COLOR]**Files which may need to be edited include /boot/grub/menu.lst and /etc/fstab. It's a good idea to back up these important files first:
```
sudo cp /etc/fstab /etc/fstab.bk1
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bk1
```
**[COLOR="Sienna"]To find out the UUID for each partition[/COLOR]**, in a terminal type:
```
sudo blkid
```
[INDENT]This will show the current UUID and the device designation for each drive recognised by the BIOS. The partition does not need to be mounted - it will appear here in any case.[/INDENT]

**[COLOR="Sienna"]To list all partitions on all drives:[/COLOR]**
```
sudo fdisk -l
```
[INDENT]This will show the partition information for each drive, and each partition. You can recognise which partition is which on the basis of its size, format and the drive designation. Once again, the partition does not need to be mounted; all partitions will be listed irrespective. The 'fdisk' command does not show the UUID of partitions but we already have that from the 'sudo blkid' command.[/INDENT]

**[COLOR="Sienna"]To find out where partitions are mounted now:[/COLOR]**
```
mount
```
**[COLOR="Sienna"]To show/edit default mount points:[/COLOR]**
```
cat /etc/fstab
sudo gedit /etc/fstab 
```
[INDENT]This will show where partitions are mounted during boot. You may wish to use a text editor other than gedit of course (eg kate, mousepad, vi, nano, mcedit etc). The UUID or device name shown in the relevant line in fstab must correlate with the partition information given by 'fdisk' and 'blkid'.[/INDENT]

**[COLOR="Sienna"]To show/edit where Grub is directing the boot process:[/COLOR]**
```
cat /boot/grub/menu.lst
sudo gedit /boot/grub/menu.lst
```
[INDENT]Towards the end of the menu.lst file you will see entries correlating to those you see in Ubuntu's start up or boot menu, (which only appears if enabled). The UUID for the respective partition, which appears in /boot/grub/menu.lst, must be that shown by 'sudo blkid'. 

[COLOR="Sienna"]**Note:**[/COLOR] Drive and partition numbering in Grub language starts at 0, whereas the numbering for the Ubuntu operating system starts at "a" or 1. Thus "root (hd0,0)" would be Grub's reference to the first partition on the first drive, ie device "/dev/sda1". Likewise for example "root (hd1,2)" would refer to "/dev/sdb3".[/INDENT] 


**[COLOR="Sienna"]Some examples from my own laptop:[/COLOR]**

Extract from output of '[COLOR="Sienna"]sudo blkid[/COLOR]':
```
/dev/sda1: UUID="73d8bfea-01e8-4f65-8efe-99265ce849db" TYPE="ext2" 
/dev/mmcblk0p1: UUID="24672713-fb81-47f5-8190-f8f88529ac44" TYPE="ext2" 
/dev/sdb1: LABEL="LaCie" UUID="6853-5BA9" TYPE="vfat" 
/dev/sdb2: UUID="c85eeef7-1599-4be8-a5b8-9d3f673db526" TYPE="ext2" 
```
[INDENT]Shows me the UUID and format type for the partitions on several disks on my  laptop. 
[/INDENT]
Extract from output of '[COLOR="Sienna"]sudo fdisk -l[/COLOR]':
```
Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a34c8

Device Boot Start  End Blocks Id System
/dev/sda1 *  1  981 7879851 83 Linux

(Other lines deleted for brevity)
```
[INDENT]Shows me the size and format information for my partitions (only "/dev/sda1" is shown here). [/INDENT]

Extract from output of '[COLOR="Sienna"]mount[/COLOR]':
```
/dev/sda1 on / type ext2 (rw,noatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/mmcblk0p1 on /home type ext2 (rw,noatime)
/dev/sdb1 on /media/sdb1 type vfat (rw,noexec,nosuid,nodev,dmask=0000,fmask=1111,uid=1000,gid=1000)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

(Other lines deleted for brevity)
```
[INDENT]Shows (amongst other things) that my partition /dev/sda1 is mounted on the root file system "/" and that my /dev/mmcblk0p1is mounted on "/home". [/INDENT]

Extract from output of '[COLOR="Sienna"]cat /boot/grub/menu.lst[/COLOR]':
```
(Lots of lines deleted for brevity)
title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=73d8bfea-01e8-4f65-8efe-99265ce849db ro quiet
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=73d8bfea-01e8-4f65-8efe-99265ce849db ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
(Other lines deleted for brevity)
```
[INDENT]Here: 
[LIST]
[*]'title' is the relevant line as displayed in the Grub menu
[*]'root' is the partition where grub will look for the boot files (and remember (hd0,0) refers to /dev/sda1)
[*]'kernel' is the path where grub will look for the kernel file
[*]'initrd' is the path where grub will look for the file system image file
[/LIST][/INDENT]
**[COLOR="Sienna"]If Grub throws up an error 15 or 17:[/COLOR]**
[INDENT]We can confirm whether the boot partition shown in 'cat /boot/grub/menu.lst' has the correct UUID. It must be the same as that from the output of 'sudo blkid'. 

We can use a live CD to check that the kernel files are actually located where Grub is looking for them. How? In this example, I would use 'sudo fdisk -l' to determine where the Ubuntu operating system is located (usually this will not be difficult). In this case it is /dev/sda1. Then three steps: I would create a mount point, mount the partition, and list the /boot directory to see if the kernel image files are there:
```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
ls /media/sda1/boot/
```
We can use Catlett's [guide to restore Grub]("http://ubuntuforums.org/showthread.php?t=224351"). [/INDENT]

**[COLOR="Sienna"]Grub errors - what do they mean?[/COLOR]** 

For easy reference, here is the output of 'info grub' for some errors I have seen in this forum:
```
15 : File not found
This error is returned if the specified file name cannot be found,
but everything else (like the disk/partition info) is OK.
```
```
17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the
filesystem type cannot be recognized by GRUB.
```
```
22 : No such partition
This error is returned if a partition is requested in the device
part of a device- or full file name which isn't on the selected
disk.
```
**[COLOR="Sienna"]Some useful links: [/COLOR]**

[LIST]
[*]About Grub (thanks, Herman): [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[*]How-to restore Grub (thanks, Catlett): [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[*]How-to fstab (thanks, Bodhi.Zazen): [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)
[/LIST]

Hope this is useful. Corrections and comments welcome of course. 

Cheers, Pat.

---

