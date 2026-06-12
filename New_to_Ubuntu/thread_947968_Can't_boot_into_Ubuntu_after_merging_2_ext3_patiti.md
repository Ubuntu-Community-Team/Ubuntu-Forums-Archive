---
title: "Can't boot into Ubuntu after merging 2 ext3 patitions, Windows works"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by mikecomua on 2008-10-14
OK.. So I had two Ubuntu partitions on my HDD. One Ubuntu didn't work something, and I reinstalled Ubuntu on my 20gb ext3 partition, which I made for other Linux distros.  I have an 80gb HDD, so I merged my 30gb ext3 and my 20gb ext3 to make one 50gb patition on my Live CD. It did that, however it killed my GRUB record or something, which I easily fixed. Now I can boot into Windows. My Ubuntu screen just continues with the moving slider. After booting Recovery Mode, it just froze after it said something about the CD. Any help will be greatly appreciated.

---

### Post by caljohnsmith on 2008-10-14
Most likely your UUID changed for your Ubuntu partition, so you'll need to change it in your Grub's menu.lst and your /etc/fstab. From your Live CD try:
```
sudo fdisk -l
```
Figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
sudo blkid
gksudo gedit /mnt/boot/grub/menu.lst
```
And use the output of the blkid command to figure out what your correct UUID should be, and most likely you'll need to change it in your menu.lst entries for Ubuntu. Next you'll need to fix your fstab:
```
gksudo gedit /mnt/etc/fstab
```
And make sure the Ubuntu partition and your swap have the correct UUID. If you run into any problems, please post your fstab, menu.lst, and the output of the fdisk and blkid commands. :)

---

### Post by mikecomua on 2008-10-14
Nothing changed. I found out that my /dev/sda6 UUID was set to /dev/sda7, so I corrected that
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2520    20241868+   7  HPFS/NTFS
/dev/sda3            2521        9546    56436345    5  Extended
/dev/sda5            9230        9546     2546271   82  Linux swap / Solaris
/dev/sda6            2521        9229    53889979+  83  Linux

Partition table entries are not in disk order

```

```
 menu.lst
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
# kopt=root=UUID=79d1781e-f06a-425b-88bc-46eea3982ae0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79d1781e-f06a-425b-88bc-46eea3982ae0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79d1781e-f06a-425b-88bc-46eea3982ae0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce2c4366-5731-443f-b497-62788687ae4c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ce2c4366-5731-443f-b497-62788687ae4c ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="58A14CDE014384FC" TYPE="ntfs" 
/dev/sda5: TYPE="swap" UUID="13224fb8-7d16-43de-a285-89010ab96825" 
/dev/sda6: UUID="79d1781e-f06a-425b-88bc-46eea3982ae0" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
```

```
ubuntu@ubuntu:~$ gksudo cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=79d1781e-f06a-425b-88bc-46eea3982ae0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=13224fb8-7d16-43de-a285-89010ab96825 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by Miljet on 2008-10-14
It looks like to me that your sda6 partition is not bootable. Probably when you merged the two partitions the resulting partition wasn't set to be bootable.

---

### Post by mikecomua on 2008-10-14
OH... You're right! fstab showed only my Windows partition was bootable. Can QTGrubEditor fix it?

---

### Post by caljohnsmith on 2008-10-14
In your menu.lst, it looks like you need to change your "root (hd0,6)" lines for your Ubuntu entries to use (hd0,5) which is sda6:
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		[COLOR="Red"](hd0,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79d1781e-f06a-425b-88bc-46eea3982ae0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		[COLOR="Red"](hd0,5)[/COLOR]
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=79d1781e-f06a-425b-88bc-46eea3982ae0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		[COLOR="Red"](hd0,5)[/COLOR]
kernel		/boot/memtest86+.bin
quiet
```
If you were previously booting Ubuntu with the Ubuntu entries that say they are on /dev/sda6, those entries use the wrong UUID and you would get the booting problem behavior you are seeing. Anyway, give the above a shot and let me know what happens.

---

### Post by caljohnsmith on 2008-10-14
> **Miljet said:**
> It looks like to me that your sda6 partition is not bootable. Probably when you merged the two partitions the resulting partition wasn't set to be bootable.
You don't need to set the boot flag on a partition for Grub to boot it; the boot flag is only relevant for brainless boot loaders in the MBR like Windows that merely chain load whichever partition is active, or has the boot flag set. :)

---

### Post by mikecomua on 2008-10-14
I'll still try both :)

---

### Post by mikecomua on 2008-10-14
It worked! THANK YOU!

---

### Post by caljohnsmith on 2008-10-14
That's great news, and you're certainly welcome. Cheers and have fun Ubuntu-ing. :)

---

