---
title: "Gentoo + Ubuntu dual boot"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by gsmax4 on 2008-08-08
Hi, I'm having trouble installing Gentoo on a PC that already has Ubuntu on it. When I was setting up the system, I chose GRUB bootloader even though I was already using it and Gentoo will not shou up on the list. Here is /boot/grub/menu.lst

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
# kopt=root=UUID=9556e73f-6c4a-481a-bd78-4883fd2220a2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9556e73f-6c4a-481a-bd78-4883fd2220a2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9556e73f-6c4a-481a-bd78-4883fd2220a2 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9556e73f-6c4a-481a-bd78-4883fd2220a2 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9556e73f-6c4a-481a-bd78-4883fd2220a2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

here is:
```
owner@owner-desktop:~$ sudo /sbin/fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
240 heads, 63 sectors/track, 15505 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf84ef84e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12712       15505    21122640   83  Linux
/dev/sda2   *         715        7357    50221080    7  HPFS/NTFS
/dev/sda3            7358        7454      733320    f  W95 Ext'd (LBA)
/dev/sda4            7455       12711    39742920   83  Linux
/dev/sda5            7358        7454      733288+  82  Linux swap / Solaris

Partition table entries are not in disk order

```
```
owner@owner-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             39117704   3726660  34198760  10% /
varrun                  225276       116    225160   1% /var/run
varlock                 225276         0    225276   0% /var/lock
udev                    225276        52    225224   1% /dev
devshm                  225276        56    225220   1% /dev/shm
lrm                     225276     39760    185516  18% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             49044016  48549388    494628  99% /media/hda2
/dev/sda1             20790732   1470736  18263864   8% /media/disk

```

sda1: Gentoo
sda4: Ubuntu

I can view and access the sda1 files perfectly from Ubuntu, I just can't boot into Gentoo. Thanks!

---

### Post by Crafty Kisses on 2008-08-08
You need to add Gentoo to your GRUB list manually.

---

### Post by gsmax4 on 2008-08-08
> **Codename said:**
> You need to add Gentoo to your GRUB list manually.

How do I do that? I mean, what should I enter into menu.lst?

---

### Post by Crafty Kisses on 2008-08-08
> **gsmax4 said:**
> How do I do that? I mean, what should I enter into menu.lst?

It would go something like this:
```
title        Gentoo (edit to your liking)
root        (hd0,5) (or whatever HDD Gentoo is on)
kernel        (add the kernel path, it should be in /boot somewhere) root=/dev/sda6 ro single
initrd        (add the path to Gentoo's initrd)
quiet
savedefault

```

Then you should be set, any problems let me know.

---

### Post by Dylock on 2008-08-08
Here is the gentoo resource for GRUB: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#grub](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#grub)
I just quickly looked over it but that should help you make your grub entry.

---

### Post by Crafty Kisses on 2008-08-08
> **Dylock said:**
> Here is the gentoo resource for GRUB: [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#grub](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?full=1#grub)
I just quickly looked over it but that should help you make your grub entry.

That's the documentation I was looking for, thanks for that Dylock.

---

### Post by Dylock on 2008-08-08
Man everyone messing with Gentoo lately is really making me want to jump back into it, mmmmmm compiling everything *drool*

---

### Post by Catalyst2Death on 2008-08-08
You should also be careful which menu.lst is active.  If you let gentoo do anything automatic, then it is probably flagged to boot, and so you need to edit that menu.lst.  Otherwise, gentoo thought it installed GRUB and made a menu.lst, but the ubuntu partition remained in control (ie bootable) in which case, you need to add Gentoo to the menu.lst in the boot directory of the ubuntu install. You should be able to just copy past the boot commands right out of the Gentoo install's menu.lst  I'm assuming that if your installing Gentoo, you're probably following what I'm saying if not, holler and I'll clarify.

As I re-read this I realize that, if ubuntu is still showing up, it is still in control. Then you just need to copy the relevant lines from the Gentoo menu.lst to the current one (when booted into Ubuntu)  If it is the other way around (Ubuntu not showing up) then your on the Gentoo menu.lst and you need to pirate your ubuntu settings the other way around.

---

### Post by gsmax4 on 2008-08-08
Thanks for everyones posts, I added (directly from /media/disk/boot/grub):
```
splashimage=(hd0,5)/boot/grub/splash.xpm.gz
title=Gentoo Linux
root (hd0,0)
kernel /boot/kernel-genkernel-x86-2.6.24-gentoo-r5 root=/dev/ram0 init=/linuxrc ramdisk=8192 real_root=/dev/sda1  doscsi
initrd /boot/initramfs-genkernel-x86-2.6.24-gentoo-r5
```

But I 'm getting an "error 22" message saying it can't read the  partition or something like that.

---

### Post by gsmax4 on 2008-08-08
Does anyone know how to find out what x is in (hd0, x)??

---

### Post by Crafty Kisses on 2008-08-08
> **gsmax4 said:**
> Does anyone know how to find out what x is in (hd0, x)??

You might be able to find out using gparted.

---

### Post by zvacet on 2008-08-08
In your menu list below windows entries add 

title         Gentoo
rootnoverify  (hd0,0)
chainloader +1

and see if it works.

---

### Post by gsmax4 on 2008-08-08
> **zvacet said:**
> In your menu list below windows entries add 

title         Gentoo
rootnoverify  (hd0,0)
chainloader +1

and see if it works.

OK, I tried:
```
title         Gentoo
rootnoverify  (hd0,2)
chainloader +1
```

but now it just says "starting up" but nothing else after that.

---

### Post by Catalyst2Death on 2008-08-08
chainloader+1 tells grub to let the next bootloader to run down the line.  In your case it looks on (hd0,2) This is the first hard-drive and 3rd partition.  (always remember to count from 0!)  Then it looks there for a bootloader (grub again) and tries to launch that menu.lst  So, you need to make sure that theres a grub install there and edit the /boot/menu.lst to point to the correct areas.  you can do this in ubuntu by mounting the partition under media and editing that way:

```
$sudo mkdir /media/gentoo
$sudo mount /dev/sda3 /media/gentoo #may be hda3 in your case, not sure
$sudo nano /media/gentoo/boot/grub/menu.lst
```

have you tried booting into a live cd and flagging your gentoo partition as bootable?  Then restart and see if you can boot into gentoo.  If you can't boot at all go back to the live cd and flip the ubuntu partition back to bootable.  You can't use chainloader if gentoo won't boot when its allowed to bootable...

---

