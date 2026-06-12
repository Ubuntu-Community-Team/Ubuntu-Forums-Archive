---
title: "Adding a kernel to menu.lst?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by The Tronyx on 2008-05-04
Hi everyone.  I recently noticed that my desktop was no longer using my ATI drivers but rather Mesa ones.  This eventually lead me to discover that grub was booting the .14 kernel rather than the .16 which is what I want to boot. 

The problem is that it is not in my menu.lst file.  Its contents are:

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
# kopt=root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro quiet nosplash
initrd		/boot/initrd.img-2.6.24-14-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=6b9b94ec-69d9-4098-8eaf-b90e8a1719b0 ro single
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

Synaptic and update-grub show me that the .16 kernel is there.  The results of sudo update-grub are below

```

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/vmlinuz-2.6.24-14-generic
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/vmlinuz-2.6.22-12-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

But unfortunately it does not add the 16 kernel to menu.lst.  Any ideas?  I tried reinstalling the kernel image from the repos with no luck.  Any help is much appreciated.  

Thanks!

---

### Post by otrojake on 2008-05-04
I'd try manually editing the .lst file.  ```
sudo gedit /boot/grub/menu.lst
``` and replace all the references to .14 with .16

---

### Post by annda on 2008-05-04
umm, i would add the entry, not replace it.

---

### Post by bobnutfield on 2008-05-04
> umm, i would add the entry, not replace it

You will be very wise to take annda's advice.  Always have an alternative working kernel available in your menu.lst.

---

### Post by otrojake on 2008-05-04
You heard the guys.  They probably have a better idea than I do. :)

---

### Post by The Tronyx on 2008-05-04
Works like a charm.  Thanks for your help!

---

