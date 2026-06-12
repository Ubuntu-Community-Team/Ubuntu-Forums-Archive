---
title: "[SOLVED] Ubuntu installed first XP not loading"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by p3la on 2008-11-11
I get the Error:11 Unrecognized Device String when I run it from the menu.
I resized ubuntu with gparted, made a new partition for xp. installed xp, fixed the grub loader to load ubuntu. Then i tried to edit the menu.lst to get windows xp to boot.

here is my fdisk-1

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x000aace0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8334    62998866   83  Linux
/dev/sda2   *        8335        9909    11907000    7  HPFS/NTFS
/dev/sda3            9910       10338     3229065    5  Extended
/dev/sda5            9910       10338     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031798784 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      392206      967564   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(392205, 19, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(967563, 8, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       85025     1060846   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(85024, 30, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1060845, 20, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      942481     1918302   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(942480, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1918301, 7, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1     1833280  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1833279, 15, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

and my menu.lst

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
# kopt=root=UUID=2afc6b29-b1ca-4774-aa70-44cbe93376df ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2afc6b29-b1ca-4774-aa70-44cbe93376df ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2afc6b29-b1ca-4774-aa70-44cbe93376df ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2afc6b29-b1ca-4774-aa70-44cbe93376df ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2afc6b29-b1ca-4774-aa70-44cbe93376df ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
map (hd0, hd1)
map (hd1, hd0)
rootnoverify (hd1,0)
chainloader (hd*,*)+1
```

---

### Post by randy78 on 2008-11-11
Try this: 
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

EDIT: it doesn't matter what you call it in the title ;)

---

### Post by p3la on 2008-11-11
I also tried 
title Microsoft Windows XP Professional
root (hd0,1)
makeactive
chainloader +1 

i don't want it to be default thought. i want ubuntu to be default. should i still try it?

---

### Post by randy78 on 2008-11-11
Using what I gave you, Ubuntu will be default.

---

### Post by p3la on 2008-11-11
ahhh ic thank you. will try right now.

---

### Post by randy78 on 2008-11-11
You're welcome :)

---

### Post by p3la on 2008-11-11
thank you. it worked! im in windows xp right now. good nite.

---

### Post by randy78 on 2008-11-11
Cool!

Please mark this thread as solved using the Thread Tools menu at the top of the post :D

---

