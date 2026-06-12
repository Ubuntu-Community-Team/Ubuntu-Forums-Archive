---
title: "Help me fix this weird booting Prob;)"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by RichieTrixs on 2008-05-15
Ok i run a dual boot vista & ubuntu 8.0.4 hardy heron.
When i boot up from a cold start i get a choice to use ubuntu or vista,when i start ubuntu it boots up into a ubuntu boot gui and then goes into a buzybox v1.1.3 and under that it has a prompt that reads {initramfs} ... thats all no boot directly into ubuntu ;(

But ! if i boot into vista from a cold start and i restart the pc from vista i get the same dual boot choice screen and i choose ubuntu it boots into ubuntu with no problem ;) so it seems to only work when i boot into vista and do a restart!

I would like to fix this error.

Best,
Richie

---

### Post by phidia on 2008-05-15
Look at the most recent messages in /var/log/system if there's a boot log there you can look at that and perhaps dmesg too.

---

### Post by RichieTrixs on 2008-05-15
is this a common problem after a live install thru vista ?

---

### Post by phidia on 2008-05-15
> **RichieTrixs said:**
> is this a common problem after a live install thru vista ?
 I don't know really since I have never installed through windows. 
How many hard drives are in this computer? You could post the output of sudo fdisk -l (typed in terminal) and also post your /boot/grub/menu.lst

---

### Post by spiderbatdad on 2008-05-15
This is a common problem, I believe, where windows is in suspend/hibernation or not shut down 'cleanly' prior to booting into Ubuntu.

---

### Post by RichieTrixs on 2008-05-15
1 harddrive,:from terminal:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe10f35f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30402   244196682    7  HPFS/NTFS

Disk /dev/mmcblk0: 2007 MB, 2007498752 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008db3d

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         225     1807281   83  Linux
/dev/mmcblk0p2             226         244      152617+   5  Extended
/dev/mmcblk0p5             226         244      152586   82  Linux swap / Solaris
....
....
:from munu.lst
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
# kopt=root=UUID=6F29C6544FB2D328 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6F29C6544FB2D328 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6F29C6544FB2D328 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/mmcblk0p1.
title		Ubuntu 8.04 (8.04) (on /dev/mmcblk0p1)
root		
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/mmcblk0p1 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by RichieTrixs on 2008-05-15
anybody?

---

