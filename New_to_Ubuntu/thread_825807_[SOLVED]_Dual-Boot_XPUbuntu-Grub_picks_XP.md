---
title: "[SOLVED] Dual-Boot XP/Ubuntu-Grub picks XP"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by moocow1452 on 2008-06-11
Hi, all. I was trying to mess around with my Dual Boot system, and now I can't get it to work with XP. I used GParted to name my Ubuntu Partition the Root, and it works fine. But if I pick XP, then when I reboot, the system goes to XP and bypasses Grub somehow.

---

### Post by logos34 on 2008-06-11
even if you had 'savedefault' feature enabled, the grub menu would (should) still show

post your grub config file:

cat /boot/grub/menu.lst

---

### Post by Duck2006 on 2008-06-11
and

sudo fdisk -l

---

### Post by moocow1452 on 2008-06-11
Sorry it took so long, couldn't get back to my computer all day. 


Grub:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=0b1f7376-5dc4-4802-a271-ca8f17274b17 ro

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

title		Ubuntu 8.04, Hardy Heron
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=0b1f7376-5dc4-4802-a271-ca8f17274b17 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Media Center 2005
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

And Fdisk
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ea4f703

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6136    49287388+  83  Linux
/dev/sda2            6137       12272    49287420    7  HPFS/NTFS
/dev/sda3           12273       13995    13839997+   7  HPFS/NTFS
/dev/sda4           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

```

Anything substancial?

---

### Post by meierfra. on 2008-06-11
I think this is what is going on:

Grub is installed on the boot sector of Ubuntu Partition and not in the MBR.  The MBR always looks for the partition with the boot flag.  If you boot into windows, the "makeactive" statement in the grub menu, sets the boot flag on the Windows partition. So after reboot, you boot into Windows. It seems to me that you fix this problem by setting the boot flag to the Ubuntu partition. Is that right? Is that what you meant with "I  used GParted to name my Ubuntu Partition the Root"?


If my analysis is correct you have two ways to fix the problem:

1) ```
gksudo gedit /boot/grub/menu.lst
```

and remove the "makeactive" from the windows item.


2)  Install grub to the MBR:

```
sudo grub
```

and at the grub prompt:


```
root (hd0,0)
setup (hd0)
quit
```

---

### Post by Victormd on 2008-06-11
I'm not sure if I understood your problem. You can boot both to Ubuntu and XP, but when you select XP, on the next boot it skips grub? Is that it?
Well, either way, you can use [SuperGRUB]("http://www.supergrubdisk.org/") to fix this.

---

### Post by moocow1452 on 2008-06-11
Thanks, I was just copy-pasting, so that makeactive must of slipped by.

---

