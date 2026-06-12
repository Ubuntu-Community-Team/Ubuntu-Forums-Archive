---
title: "Dual Boot Trouble"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by wildcat1980 on 2008-05-17
I just installed the newest version of Ubuntu.  On the same drive I have Windows XP.  I had the drive partitioned through the Ubuntu set-up.  I can access Ubuntu, that it boots to, but when I decide to boot into Windows, all I get is a black screen with the phrase     

Now Starting.........

But it never does!  I've rebooted several times with the same result.  I can see all my files and stuff that I have on xp still there. 
IN addition, I've tried changing the boot order as well, so by default it would start to Windows, but it continues to hang on that black screen.
Any ideas?

---

### Post by meierfra. on 2008-05-17
post the output of 

```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

(both "l" are lowercase "L")

---

### Post by wildcat1980 on 2008-05-18
Here is the requested information.....

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d567d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5751    46194876    7  HPFS/NTFS
/dev/sda2            5752       19457   110093445    5  Extended
/dev/sda5            5752       19174   107820216   83  Linux
/dev/sda6           19175       19457     2273166   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7668    61593178+   c  W95 FAT32 (LBA)

and then.....

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7d567d56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5751    46194876    7  HPFS/NTFS
/dev/sda2            5752       19457   110093445    5  Extended
/dev/sda5            5752       19174   107820216   83  Linux
/dev/sda6           19175       19457     2273166   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7668    61593178+   c  W95 FAT32 (LBA)
corey@corey-desktop:~$ cat /boot/grub/menu.lst
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
default		4

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
# kopt=root=UUID=bb35ae08-b04f-416a-8502-cb5498ff0316 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bb35ae08-b04f-416a-8502-cb5498ff0316 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=bb35ae08-b04f-416a-8502-cb5498ff0316 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Thanks in advance!

---

### Post by tamoneya on 2008-05-18
that all seems in order.  If you can please mount /dev/sda1 ( your windows partition and post boot.ini.  Here are the terminal commands if you dont know how to do that.```
sudo mkdir /windows
sudo mount -t ntfs /dev/sda1 /windows
cd /windows
nano boot.ini
```

---

### Post by zvacet on 2008-05-18
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

Replace 


title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

with 

title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
makeactive
chainloader +1

Save and close file.After reboot you should be able to boot in Windows.

---

