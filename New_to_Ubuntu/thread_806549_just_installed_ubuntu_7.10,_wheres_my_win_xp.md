---
title: "just installed ubuntu 7.10, wheres my win xp??"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by arikun on 2008-05-25
i just installed 7.10, followed the directions from the cd. but where is my windows xp?? please help!!

---

### Post by Inxsible on 2008-05-25
Do you see a grub menu - where you can select the OS you want to log into ?

What method did you use to partition your hard drive during the installation of Ubuntu?

---

### Post by skymera on 2008-05-25
can you post the output of

```
 cat /boot/grub/menu.lst 
```

---

### Post by bumanie on 2008-05-25
Post the output of > sudo fdisk -l You can do this from within ubuntu or off the live cd if ubuntu doesn't boot.

---

### Post by misfitpierce on 2008-05-25
Those commands given to you are to be typed in Terminal...

Applications - Accessories - Terminal

Thats how you get to terminal... Type commands shown and post the output in here.

---

### Post by arikun on 2008-05-25
>.< bad feelin commin on....

> **skymera said:**
> can you post the output of

```
 cat /boot/grub/menu.lst 
```

enter that in applications, accessories, terminal? if so...
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=04565a4c-abe0-417d-83f5-76056cd8564e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=04565a4c-abe0-417d-83f5-76056cd8564e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=04565a4c-abe0-417d-83f5-76056cd8564e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by arikun on 2008-05-25
> **bumanie said:**
> Post the output of  You can do this from within ubuntu or off the live cd if ubuntu doesn't boot.

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Inxsible on 2008-05-25
that command is ```
sudo fdisk -l
``` -l is lowercase L

---

### Post by arikun on 2008-05-25
> **Inxsible said:**
> that command is ```
sudo fdisk -l
``` -l is lowercase L


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30048   241360528+  83  Linux
/dev/sda2           30049       30401     2835472+   5  Extended
/dev/sda5           30049       30401     2835441   82  Linux swap / Solaris

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         993     1000912+   6  FAT16

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006030

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          13      104391   83  Linux
/dev/sdf2              14       19457   156183930    7  HPFS/NTFS



yea...i think i screwed myself over..v.v

---

### Post by Inxsible on 2008-05-25
> **arikun said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30048   241360528+  83  Linux
/dev/sda2           30049       30401     2835472+   5  Extended
/dev/sda5           30049       30401     2835441   82  Linux swap / Solaris

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         993     1000912+   6  FAT16

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006030

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1          13      104391   83  Linux
/dev/sdf2              14       19457   156183930    7  HPFS/NTFS



yea...i think i screwed myself over..v.vyup. I guess you did. You only have 1 NTFS partition where you most likely have Vista. So no XP !!

---

### Post by arikun on 2008-05-25
'Vista'? 
so, any idea on how to get it back?

---

### Post by bumanie on 2008-05-25
You could try test disk from [here]("http://www.cgsecurity.org/wiki/TestDisk") Read the documentation carefully. It is not the most expansive, but it has saved other's before. It is a data/partition recovery program that can run from a live cd. Could also try photorec (same kink) or trinity rescue disc which has a ntfs undelete program on it - it also is a live cd. Good luck. Try to leave that drive unwritten to until you have the rescue discs. There is also ntfsprogs in synaptic that has a ntfsundelete program also. Unfortunately, I am not expert in using these, but you can't really end up any worse than you are now, so it's worth a go. With ntfsundelete, you have to send the output to a partition other than the one where you are retrieving the information from. Read up on all these before you decide which one to follow/try. Good luck.

---

### Post by skymera on 2008-05-25
Adding Windows to GRUB is very easy.

at the bottom below ##END OF AUTOMAGIC KERNEL LIST add this (change accordingly)

```

title		Windows XP Media Center Edition 2005
root		(hd1,0)
chainloader +1
makeactive
map (hd0) (hd1)
map (hd1) (hd0)

```

Change the name and the drives according to yours.
Save grub and XP should boot.

---

