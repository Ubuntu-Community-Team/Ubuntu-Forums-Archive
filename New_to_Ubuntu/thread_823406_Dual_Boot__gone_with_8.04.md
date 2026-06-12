---
title: "Dual Boot  gone with 8.04"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by suffring on 2008-06-09
Hi,  I've just updated to 8.04 from 7.04 thru 7.10.  My dual boot with Win98 under 7.04 was working OK.  Now, when I select Win98 from the grub list, I get the following; "Quit one or more memory resident  programmes or remove unnecessary utilities from your config.sys & autoexec.bat files and restart your computer".

I'm thinking that Grub is working and that this is a problem with Win98.  Any ideas how to fix it would be much appreciated.  Thanks,

---

### Post by abhiroopb on 2008-06-09
type the following into the terminal

sudo fdisk -l

paste the output

then type in:
gksudo gedit /boot/grub/menu.lst

and paste whatever is in that file here.

---

### Post by suffring on 2008-06-09
Thanks.  I've posted the two results below:
Thanks again for the help.


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d102e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2967    23832396    c  W95 FAT32 (LBA)
/dev/sda3            2981        3045      522112+  82  Linux swap / Solaris
/dev/sda4            3046        4865    14619150    f  W95 Ext'd (LBA)
/dev/sda5            3046        4865    14619118+  83  Linux
john@J-L:~$ 


And..........


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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 rogksudo gedit /boot/grub/menu.lst

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-genericgksudo gedit /boot/grub/menu.lst
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9846c4bf-e9c6-443b-ac1f-e8ed050c4fa5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by suffring on 2008-06-15
AH!  Got it!  The problem lies in Windows (specifically Win98) not Ubuntu.  The problem also lies in the fact that I forgot to mention that at the same time as updating to Hardy, I also upgraded my RAM from 256 to over 2 Meg and which, unbeknowns to me, Win98 just can't take that amount of Ram.  I had to take out the extra ram to be able to start win98, change the ram limit in the MSCONFIG file to 512 and then put the extra ram back.

---

