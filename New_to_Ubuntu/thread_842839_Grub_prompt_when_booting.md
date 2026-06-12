---
title: "Grub prompt when booting"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by niranjanpm on 2008-06-27
Hi
I am new to linux, ubuntu and this forum. I installed Ubuntu 8.04 today. 

In step 7 of the installation i had to choose a device to install bootloader on, and default it was hd0, i installed with that setting. The OS did not startup on booting and instead there was this GRUB> command line prompt there. I re-installed ubuntu, this time i chose /dev/sdb7 (the partition where ubuntu is intalled on). The same grub problem is occurring. I also have Windows XP installed on my pc, and i cant boot to both xp or ubuntu(without the liveCD).
   
From other threads, i followed some commands,
   sudo fdisk -l
   sudo mkdir /media/sdb
   sudo mount -t ext3 /dev/sdb7 /media/sdb
   cd /media/sdb/boot/grub
and got to the file called menu.lst

I am totally stuck here, dont know what to do, the grub prompt still comes on booting.
My windows is loaded on sdb1 partition. Ubuntu on sdb7. There is also another hard disk sda. I dont know which of them is hd0 or hd1, so dont know if i made any mistake during install or anything.

Please Help.

---

### Post by logos34 on 2008-06-27
Post the menu.lst so we can take a look at it.  It will show which disk you're booting from (i.e. which is hd0 and hd1).

Post the fdisk output as well.

In the meantime you could try reinstalling grub to the MBR:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by kansasnoob on 2008-06-27
The way grub numbers things if you have only one hard drive it's (hd0, ?). A second hard drive is (hd1, ?). Basically Grub starts with the number 0 instead of the number 1.

(BTW, GRUB doesn't care if it's an sda or hda and neither do you at this point!)

Now my (?) in (hd0, ?) is the partition number. Again GRUB sees partition (sda1), or (hda1) as (0).

Clear as mud, huh?

Now, if you've fiddled a lot with GRUB the first thing you should probably do is get it back where it was!

And please tell us everything you've done from the beginning of the problem until now!

---

### Post by kansasnoob on 2008-06-27
logos34,

I hope you can just take this over, I get lost myself in menu lists without knowing the contents of partitions.

Thanks!

---

### Post by logos34 on 2008-06-27
ok, kansasnoob, but it appears you understand grub fairly well.

---

### Post by WRDN on 2008-06-27
To add, while you're trying to fix the current problem, its worth booting the Windows disk, selecting recovery console (press R) and typing "fixmbr".
This will fix the master boot record, and you can then boot automatically into Windows (it will overwrite GRUB).

---

### Post by niranjanpm on 2008-06-27
This is my fdisk -l  :

Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x007e007e



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)

/dev/sda2            2551        9729    57665317+   7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x02d202d1



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS

/dev/sdb2            5100       19456   115322602+   f  W95 Ext'd (LBA)

/dev/sdb5            5100       10198    40957686    7  HPFS/NTFS

/dev/sdb6           10199       12748    20482843+   b  W95 FAT32

/dev/sdb7           12749       15935    25599546   83  Linux

/dev/sdb8           15936       16190     2048256   82  Linux swap / Solaris

/dev/sdb9           16191       19456    26234113+  83  Linux

---

### Post by niranjanpm on 2008-06-27
ANd this is my menu.lst

#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.

# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'

# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro

#
#

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs
## ## Start Default Options ##
## default kernel options

## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option

# xenhopt=
## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0
## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true
## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro single
initrd          /boot/initrd.img-2.6.24-16-generic
title           Ubuntu 8.04, memtest86+
root            (hd1,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
chainloader     +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by kansasnoob on 2008-06-27
How many hard drives do you have?

BTW, I'm learning too.

---

### Post by niranjanpm on 2008-06-27
Two hard disks.
But both ubuntu and xp are installed on same disk.

---

### Post by kansasnoob on 2008-06-27
Can you boot either OS?

I seem to see that win is on hd(0) but ubuntu is on hd(1)?

---

### Post by kansasnoob on 2008-06-27
But you could also have issues beyond that!

I always create a hand scribed file on my spiral notebook of such stuff because I fiddle around a lot.

---

### Post by niranjanpm on 2008-06-27
No, I cant boot to either OS. The thing is, one of the hard disks is an old one from an earlier pc on which xp was installed. But my C: is on the same disk as ubuntu. So it should be that win xp(the one which i boot normally) is on hd(1) and ubuntu is also on hd(1). 
Also, when i first installed ubuntu, i had given hd(0) as the device to which boot loader should be installed and when i installed again, i set the device to /dev/sdb7/ which is the partition where ubuntu is intalled. I dont know if that makes the difference to the problem though .

---

### Post by niranjanpm on 2008-06-27
Hey,
I solved the problem :).
I installed the grub again and removed the old Windows XP part from the file menu.lst. Now its working fine, hopefully, no more issues later on. :P

I just solved the issue by exploring and reading the forums. Linux is fun.

Thanks.

---

### Post by kansasnoob on 2008-06-27
Ok, but this looks like you have win XP Home on on drive and XP pro on the other:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

You see at "root" one entry shows up as (hd0, 0) and the other shows up as (hd1, 0).

So this is complicated!

---

### Post by kansasnoob on 2008-06-27
> **niranjanpm said:**
> Hey,
I solved the problem :).
I installed the grub again and removed the old Windows XP part from the file menu.lst. Now its working fine, hopefully, no more issues later on. :P

I just solved the issue by exploring and reading the forums. Linux is fun.

Thanks.

Cool! Mark it solved!

---

### Post by logos34 on 2008-06-27
> **niranjanpm said:**
> No, I cant boot to either OS. The thing is, one of the hard disks is an old one from an earlier pc on which xp was installed. But my C: is on the same disk as ubuntu. So it should be that win xp(the one which i boot normally) is on hd(1) and ubuntu is also on hd(1). 
Also, when i first installed ubuntu, i had given hd(0) as the device to which boot loader should be installed and when i installed again, i set the device to /dev/sdb7/ which is the partition where ubuntu is intalled. I dont know if that makes the difference to the problem though .

Looks like I missed all the fun--my router and dsl modem have been acting up lately and cut my internet until I reconfigure...Anyhoo, gload you fixed it.

Just a note: as you now know, grub is on the mbr of /dev/sda--that's the boot drive.  If you ever remove it, you won't be able to boot...the fact that you put grub the second time round on the root partition sdb7 won't help--you'll have to reinstall grub to the mbr of sdb and edit menu.lst.

enjoy

---

### Post by niranjanpm on 2008-06-28
Now Ubuntu doesn't boot. I thought that when i got the menu for choosing the OS, both OS would work, XP works but when i try to boot to ubuntu, it says error 21 - disk not found or something like that.

---

### Post by logos34 on 2008-06-28
> **niranjanpm said:**
> Now Ubuntu doesn't boot. I thought that when i got the menu for choosing the OS, both OS would work, XP works but when i try to boot to ubuntu, it says error 21 - disk not found or something like that.

You need to tell us which drive is set as the boot disk in the Bios, and what Windows entry you are using.  

From these remarks:

>  I solved the problem :smile:.
I installed the grub again and removed the old Windows XP part from the file menu.lst. Now its working fine, hopefully, no more issues later on. :P

it sounds like you may be booting from sdb now...hard to tell though

Two hard drives always complicate matters (more so if they are mixed sata and ide)...One possible way to solve this once and for all is to temporarily disconnect the 80 GB drive, reinstall grub to the mbr of the 160, mount root and edit the 'groot' and 'root' lines in menu.lst to read (hd0,6), and windows to (hd0,0).  Reconnect the 80 gig and go into the bios to make sure that the 160 is still the boot drive.  

On the other hand, maybe these are both ide drives in master-slave positions...sometimes physically swapping them fixes things

---

