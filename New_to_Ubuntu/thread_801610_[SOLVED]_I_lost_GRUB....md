---
title: "[SOLVED] I lost GRUB..."
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Novega on 2008-05-20
I have 3 Hard drives- 1 with Windows XP, 1 with Hardy 32 bit and 1 with Hardy 64 bit.
I installed 32bit version on an old 30GB IDE drive, liked it and decided to install 64bit to my new SATA drive about a week later. Everything worked fine so I decided to erase my old HDD (that had Hardy32bit on it)...

I no longer have GRUB show up when booting my drive with 64 bit version. Instead, I have to set the hard drive boot preference to the drive that *had* 32bit Hardy on it...GRUB shows up with both kernel versions and my XP drive, I select the 64 bit one and it works fine.

How do I fix this?  I want to be able to boot directly off my SATA drive that has Hardy 64 on it (I would like to remove the old IDE drive that had 32 bit version on it and give it to my brother)
Thanks In Advance

---

### Post by rockerphil on 2008-05-20
ok, here's what i THINK happened, when you wiped the drive it just happened to be the drive that the GRUB boot loader was installed on. so here's what i'd do, boot in to one of your OSes and download the GRUB boot loader and install it to a floppy, that way if you ever wipe a drive again it'll still be on the floppy, but remember, you'll have to set it up to boot from your floppy drive first and you'll have to have the floppy in the floppy drive for your machine to boot, but hey, if a friend's MBR happens to get fried at least you've got the GRUB boot loader that you can take and lend a hand with

---

### Post by meierfra. on 2008-05-20
You need to reinstall grub (click on FixGrub in my signature). But you also need to edit the file /boot/grub/menu.lst. For additional  help, post the output of

```
sudo fdisk -l
```
and 

```
cat /boot/grub/menu.lst
```

(Both "l" are lowercase "L")

---

### Post by Novega on 2008-05-20
Thanks for the advice guys:) 
Here are the outputs:

sudo fdisk -l
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x159d159c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d121d11

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9598    77095903+  83  Linux
/dev/sdb2            9599       10011     3317422+   5  Extended
/dev/sdb5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7dcb7dc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3493    28057491    c  W95 FAT32 (LBA)
/dev/hdb2            3494        3649     1253070    5  Extended
/dev/hdb5            3494        3649     1253038+  82  Linux swap / Solaris

```

cat /boot/grub/menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=c700b6ba-a09d-483c-abf1-6c46824e24a5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c700b6ba-a09d-483c-abf1-6c46824e24a5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c700b6ba-a09d-483c-abf1-6c46824e24a5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6da7fb50-1a19-41d9-abde-bbea267cec68 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6da7fb50-1a19-41d9-abde-bbea267cec68 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu 8.04, memtest86+ (on /dev/hdb1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

Where do I go from here? I'm guessing the next step will be to clear out the old entries in the GRUB menu?

---

### Post by logos34 on 2008-05-21
write grub to your sata linux drive MBR:
[B]
sudo grub-install /dev/sdb
[/B]
Edit menu.lst -- take out the hdb1 entries, and change the **root** and **groot** lines from (hd2,0) to **(hd0,0)**.  Shut the computer down.  Remove the ide drive.  Then reboot, go into the Bios and set sdb drive first in hard disk boot order.

Hopefully that will do the trick

---

### Post by rburkartjo on 2008-05-21
nov try this
After checking out the options, I found the one by Searchme2 most easy for me to use - and it worked for me. Here is the part I actually used ( with my Ubuntu live cd inserted ) - 

How to restore Grub from a live Ubuntu cd.
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.


KB

the above was posted at from tech board 11 linux stuff

[http://tekboard.activeboard.com/index.spark?forumID=118217&p=1](http://tekboard.activeboard.com/index.spark?forumID=118217&p=1)
cheesemaker

---

