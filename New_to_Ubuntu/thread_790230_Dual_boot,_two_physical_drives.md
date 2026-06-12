---
title: "Dual boot, two physical drives"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by prcm311 on 2008-05-11
Looking for some help with a new installation of Windows XP.  I was running Ubuntu 8.04 with a virtual machine of XP but now I need to boot to a full version.  I started by unplugging my Ubuntu drive so XP wouldn't write over GRUB.  This worked and I've been able to configure both /etc/fstab and /boot/grub/menu.lst to where I want them.  However when I select Windows XP at the Grub menu I just get "Starting up..." and nothing happens.  Below are the two configuration files, what am I doing wrong?

**/boot/grub/menu.lst**
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
color cyan/blue white/blue

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
# kopt=root=UUID=cd474ecb-4747-4f18-be8d-b1e2c57acb79 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cd474ecb-4747-4f18-be8d-b1e2c57acb79 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cd474ecb-4747-4f18-be8d-b1e2c57acb79 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cd474ecb-4747-4f18-be8d-b1e2c57acb79 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=cd474ecb-4747-4f18-be8d-b1e2c57acb79 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title           _.-/'\-._.-/'\-._.-/'\-._.-/'\-._.-/'\-._.-/'\-._.-/'\-._
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1
```

**/etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cd474ecb-4747-4f18-be8d-b1e2c57acb79 	/               ext3    defaults,errors=remount-ro 	0       1
# /dev/sda4
UUID=5389419d-83f4-443f-9086-7047346259e7 	/media/storage  ext3    defaults        		0       2
# /dev/sdb1
UUID=260CAE010CADCBDD 				/media/virtual  ntfs    defaults,umask=007,gid=46 	0       1

##ADDED
# /dev/sdb2
UUID=a1651aae-3fbc-4fb1-b142-6d0b313be315 	/media/server  	ext3    defaults        		0       2
# /dev/sdc1
UUID=128e72ce-f2a0-4582-bda5-06d1afb956f3 	/media/backup  	ext3    defaults        		0       2

# /dev/sda2
UUID=56b8b94b-a5c2-4c9f-9fd1-4a4b6d70c4bb 	none            swap    sw              		0       0


/dev/scd0       				/media/cdrom0   udf,iso9660 user,noauto,exec 		0       0
```

---

### Post by bumanie on 2008-05-11
post the > output of sudo fdsik -l please.

---

### Post by prcm311 on 2008-05-11
```
aaron@aaron-desktop:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042781

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7833    62918541   83  Linux
/dev/sda2            7834        8420     4715077+  82  Linux swap / Solaris
/dev/sda4            8421       91201   664938382+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5605191f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sdb2            5223       38913   270622957+  83  Linux

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14691468

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   83  Linux

```

---

### Post by prcm311 on 2008-05-11
I've also tried different hard drives in menu.lst.  But shouldn't it be hd1,0 according to fstab?

---

### Post by Fenris_rising on 2008-05-11
hi there

i have 2 HDD with ubuntu on one and XP on the other. @ boot i hit F8 on my keyboard to get to a boot option screen (part of my mainboards BIOS i think) and i can pick which HDD to boot. May not be an option on your PC but just check if there is any such option on it.

---

### Post by bumanie on 2008-05-11
Windows does not like booting from a second drive. The way to sometimes trick windows is to add this to you /boot/grub menu.lst between 'makeactive and chainloader' so that it looks like this below:
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
The other problem may be that both sda1 and sdb1 have boot flags. I know from my own machine with the drives the other way around (ie xp sda1, ubuntu sdb1), that xp is the only with a boot flag. Anyway try the map commands first and you can tackle other issues later. If it were me I'd be tempted to change bios so that sdb1 is booted first and remove the boot flag from ubuntu - but I'm not 100% sure that is the correct way to go about things. Also if you did that you would have to edit /boot/grub menu.lst again to reflect the change in the drive boot order and their respective partition designations. It's much easier to have windows installed on the primary drive. I think doing that and reinstalling grub would have been less of a headache.

---

