---
title: "windows xp partition not bootable, error 22"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by Elaineg1979 on 2008-09-28
Hi there!
I am completely new to Ubuntu (2nd day) and I love it.  Ubuntu will be my primary OS.  However, I would like to know where my windows xp partition went.  I spent hours yesterday entering commands and I have some info that helped me a little (although I learned a lot), but maybe you all can help out.  

Also, I have a windows folder that appeared when i used the mount command, and I placed it on my desktop.  It has thousands of files, and when I boot up the computer on GRUB I see windows xp, click on it, and the gateway icon does not have the xp symbol then it goes to a blue screen and says error 22.  Windows folder is on ubuntu, any way to make it visible, either on Ubuntu or a separate boot?

I typed in this code 

[HTML]sudo cp /boot/grub/menu.lst  /boot/grub/menu.lst.bak <-- make a backup copy just in case...
gksudo gedit /boot/grub/menu.lst[/HTML]

and got this:


[HTML]
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
# kopt=root=UUID=f85034aa-94a7-46d4-ad97-b83b65951f9a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f85034aa-94a7-46d4-ad97-b83b65951f9a ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f85034aa-94a7-46d4-ad97-b83b65951f9a ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/HTML]

when I typed sudo fdisk -l I got:


elaine@elaine-desktop:~$ sudo fdisk -l
[sudo] password for elaine: 

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10558    84807103+  83  Linux
/dev/sda2           10559       20023    76027612+   5  Extended
/dev/sda5           19840       20023     1477948+  82  Linux swap / Solaris
/dev/sda6           10559       19655    73071589+  83  Linux
/dev/sda7           19656       19839     1477948+  82  Linux swap / Solaris

Partition table entries are not in disk order
elaine@elaine-desktop:~$ 


I am pretty sure that windows is in /dev/sda1

---

### Post by Elaineg1979 on 2008-09-28
Tried to upload a screenshot of the windows folder but could not do it.

---

### Post by kansasnoob on 2008-09-28
This:

> /dev/sda1 * 1 10558 84807103+ 83 Linux
/dev/sda2 10559 20023 76027612+ 5 Extended
/dev/sda5 19840 20023 1477948+ 82 Linux swap / Solaris
/dev/sda6 10559 19655 73071589+ 83 Linux
/dev/sda7 19656 19839 1477948+ 82 Linux swap / Solaris

Shows no windows.

Look at mine:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9729    47431912+   5  Extended
/dev/sda5            3825        6934    24981043+  83  Linux
/dev/sda6            6935        7175     1935801   82  Linux swap / Solaris
/dev/sda7            7176        9617    19615333+  83  Linux
/dev/sda8            9618        9729      899608+  82  Linux swap / Solaris


You see my sda1 is HPFS/NTFS, that's windows. Then I have Ubuntu 8.04 and 8.10  in an extended partition.

---

### Post by bumanie on 2008-09-28
You are getting grub error 22, because you have somehow deleted or overwritten windows.

---

### Post by Elaineg1979 on 2008-09-28
Hey guys!
Problem resolved.  I lost all my music but it was worth it.  I just reinstalled xp and ubuntu on cd during bootup.  Anyway, hope you all have a great day!

---

