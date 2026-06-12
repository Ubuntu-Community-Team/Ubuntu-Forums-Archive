---
title: "[SOLVED] Grub to xp"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by shadowber on 2008-09-21
I recently tried to install xp on another partition, and lost Grub. I did a little searching on the forums, and found a way to "reinstall" grub, but I don't know how to make it so that I can log onto winxp as well...(I use Ubuntu primarily, but would like to do some things in xp)

---

### Post by cartisdm on 2008-09-21
If you reinstall the grub, XP should be a choice listed at the bottom of your screen.  Just press down a few times to highlight it

---

### Post by sayakb on 2008-09-21
Download super grub disk ([http://supergrubdisk.org](http://supergrubdisk.org))
Burn the ISO (4-5 MB in size) to a CD, pop it in the CDROM and boot into the CD. You will see an option to recover/restore GRUB. Perform restoration of GRUB and reboot.
GRUB will autodetect Windows XP.

---

### Post by PocketDog on 2008-09-21
Reinstalling grub will enable dual-booting automatically. It won't kill XP

---

### Post by kansasnoob on 2008-09-21
Post the output of:

```
 sudo fdisk -l
```

That's a lower case L!

---

### Post by kansasnoob on 2008-09-21
Should also see the output of:

```
cat  /boot/grub/menu.lst
```

---

### Post by shadowber on 2008-09-21
the output of sudo fdisk -l is:```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003216a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19123   153600000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           19124       55595   292961340   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           55596       60801    41817195    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5           55596       60801    41817163+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aca06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32

```

the output of cat  /boot/grub/menu.lst is
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
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash vga=799

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro quiet splash vga=799
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro quiet splash vga=799
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro quiet splash vga=799
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro quiet splash vga=799
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.24-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro quiet splash vga=799
initrd		/boot/initrd.img-2.6.24-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro quiet splash vga=799
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=32a8b124-e553-4151-b6c6-c987e64f0cc9 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```
reinstalling grub did not work for me....

---

### Post by shadowber on 2008-09-22
bump

---

### Post by Tatty on 2008-09-22
First back up your current grub:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.list.backup
```

Then open your menu.lst file for editing as a superuser:

```
gksu gedit /boot/grub/menu.lst
```

then add the following to the bottom of the file:
```
title  Microsoft Windows XP Home
root   (hd0,0)
makeactive
chainloader +1
```

---

### Post by shadowber on 2008-09-22
Thanx, that worked!

---

