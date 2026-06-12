---
title: "Grub Error 17: Cannot mount selected partition"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by mogsmar5 on 2008-09-18
Hi

I've been sorting out my crazy partition scheme recently into a more useful one, with a new NTFS partition created for storing documents on across dual-boots. However, I can not longer boot into my Linux partition, (although my Vista partition boots fine), with GRUB giving me: Error 27: Cannot mount selected partition. Here is the output from **sudo fdisk -l**
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c7129

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28780   231175180    7  HPFS/NTFS
/dev/sda2           28781       59271   244918957+  83  Linux
/dev/sda3           59527       60801    10241437+   5  Extended
/dev/sda5           59527       59781     2048256   82  Linux swap / Solaris
/dev/sda6           59782       60801     8192000    7  HPFS/NTFS

Here is my menu.lst for the corrupted partition;

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=02502a74-eb6b-4e82-a025-3c14a69c8578 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=02502a74-eb6b-4e82-a025-3c14a69c8578 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=02502a74-eb6b-4e82-a025-3c14a69c8578 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02502a74-eb6b-4e82-a025-3c14a69c8578 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02502a74-eb6b-4e82-a025-3c14a69c8578 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

As you can see, Ubuntu is installed on Partition 2, Vista on 1. GRUB is installed on Partition 1, which is the boot-flagged partition. GRUB itself is fully functional; it doesn't need to be reinstalled, and I have have tried this lots of times anyway.

What's wrong and can I sort it out without having to reinstall Ubuntu (which I have spent a lot of time installing programs on and downloading packages I don't want to have to download again!)

---

### Post by halitech on 2008-09-18
I'm not 100% sure but I think in your entires where they say root (hd0,2) it should be root (hd0,1)

---

### Post by bobnutfield on 2008-09-18
Halitech is correct.  As it is, the partition you are trying to boot is the extended partition, which is probably empty.  Change you root entry to (hd0,1).  Grub counts partitions from 0, so /dev/sda2 is the second partition on the first hard drive and is represented in Grub as (hd0,1).

---

### Post by mogsmar5 on 2008-09-19
Thanks! I edited the file with the new info and it works fine :)

---

### Post by halitech on 2008-09-19
glad to hear you got it working :) Please remember to mark the thread solved so others will know that are searching for an answer.

---

