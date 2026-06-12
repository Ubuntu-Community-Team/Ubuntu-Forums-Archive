---
title: "Getting Windows root for GRUB"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by uhrohraggy on 2008-06-17
Hi, I know there are many tutorials on fixing the GRUB but none so far have solved the problem. I would appreciate any help. Thank you.

I have three drives: two internal SATA and one external hard drive. Below is the result of sudo fdisk -l:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023fc5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
64 heads, 63 sectors/track, 121130 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121129   244196032+   7  HPFS/NTFS

```

sda (internal) is obviously my Ubuntu, sdb (internal) holds my Windows XP partition, and sdc is the external used as a data store. The latter two only have one formatted partition per drive

after using sudo -s to go super user
i type gedit /boot/grub/menu.lst

here is the result:

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
# kopt=root=UUID=8ab7b28e-4637-48bb-8b87-a3c3f92b8fac ro

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8ab7b28e-4637-48bb-8b87-a3c3f92b8fac ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=8ab7b28e-4637-48bb-8b87-a3c3f92b8fac ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8ab7b28e-4637-48bb-8b87-a3c3f92b8fac ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8ab7b28e-4637-48bb-8b87-a3c3f92b8fac ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I know that I need to add Windows to this list akin to:

title Windows XP
root (hd#,#)
makeactive
chainloader +1

just as the document specifies, but a) I do not know the root by which to refer, or b) how to determine the root. so far the best I have gotten is the GRUB menu displaying the item, only to get Error 11, which is a problem with the connection string, presumably due to the root not being set appropriately. I have tried many combinations of roots and no avail so far. Also, the Windows drive (sdb) is flagged as boot when viewed by the partition editor, and has otherwise been untouched since installing Ubuntu. 

Thank you for any and all of your help.

---

### Post by Happy_Man on 2008-06-17
what about (1,0) ?

GRUB is odd in that the first hard drive (sda) is "0", and the second (sdb) is "1", etc. Same thing with partitions. So the logical thing is (1,0). Try and see if it works.

---

### Post by bodhi.zazen on 2008-06-17
Windows does not like being anywhere but on the first hard drive.

You will have to "map" the second hard drive to the first :

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

For basic partition information see here :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

### Post by uhrohraggy on 2008-06-17
I understand the base addressing of GRUB, and have gotten far enough that those tricks worked...kind of.

When I choose Windows XP from the list, I get:

Starting GRUB
Loading Stage2 . . .

The countdown starts up and it repeats itself over and over again, never actually beginning the bootstrap. If I hit escape during this countdown it brings me back to the GRUB menu list.

Ideas?

Thanks again for your help.

---

### Post by bodhi.zazen on 2008-06-17
Would you post your current grub stanza for windows ?

(do *not* need to see *all* of /boot/grub/menu.lst).

---

### Post by uhrohraggy on 2008-06-18
Sorry for getting back so late, just back from work.

```

title		Windows XP Professional
root		(hd1,0)
makeactive
chainloader	+1

```

---

### Post by bodhi.zazen on 2008-06-18
you need to map

[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)

---

