---
title: "[SOLVED] Number of 'media drives' on hard drive"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Stephen_A on 2008-05-29
Just installed to 8.04. There are a number of 'media drives' on the hard drive; these contain files from previous Ubuntu installations. Can anyone advise me how to remove these and return the contents to the disk space?
Thanks very much.

---

### Post by forestpixie on 2008-05-29
Can you run these in a terminal and post the results please

```
sudo fdisk -l
cat /etc/fstab
```

You can delete the old partitions and make one from the unallocated space and then add it to fstab.

---

### Post by Stephen_A on 2008-05-29
Thanks. OK. Here they are. (I get 'no such file or directory' for the 'cat' command. 


sudo fdisk-l
```

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x072f072f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         360     2891668+  83  Linux
/dev/sda2             361        4870    36226575    5  Extended
/dev/sda5            4781        4870      722893+  82  Linux swap / Solaris
/dev/sda6             361         684     2602467   83  Linux
/dev/sda7            4691        4780      722893+  82  Linux swap / Solaris
/dev/sda8             685         968     2281198+  83  Linux
/dev/sda9            4601        4690      722893+  82  Linux swap / Solaris
/dev/sda10  *        2643        4512    15020743+  83  Linux
/dev/sda11           4513        4600      706828+  82  Linux swap / Solaris
/dev/sda12            969        2566    12835903+  83  Linux
/dev/sda13           2567        2642      610438+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2087 MB, 2087976960 bytes
28 heads, 27 sectors/track, 5394 cylinders
Units = cylinders of 756 * 512 = 387072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5395     2038921+   6  FAT16
stephen@stephen-laptop:~$ 

```

---

### Post by forestpixie on 2008-05-29
Can you check that command again, also run this one

```
cat /etc/fstab
cat /boot/grub/menu.lst
```

---

### Post by Stephen_A on 2008-05-29
Sorry. My bad. ```
stephen@stephen-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda12
UUID=444ab393-75a8-4a29-ba46-353d84b5d500 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda13
UUID=23c3e08c-e93d-4f5f-af97-825b330184ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
stephen@stephen-laptop:~$ 


```

and...```
stephen@stephen-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=444ab393-75a8-4a29-ba46-353d84b5d500 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,11)

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
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=444ab393-75a8-4a29-ba46-353d84b5d500 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,11)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=444ab393-75a8-4a29-ba46-353d84b5d500 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,11)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3e854ef-5083-460e-9178-0af1df22563d ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c3e854ef-5083-460e-9178-0af1df22563d ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 7.10, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7d06de69-a88d-49d7-90c5-c778971a8d2a ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda10)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7d06de69-a88d-49d7-90c5-c778971a8d2a ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda10.
title		Ubuntu 7.10, memtest86+ (on /dev/sda10)
root		(hd0,9)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9ba15c90-740e-4c55-8ed3-d84c4597e5fb ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=9ba15c90-740e-4c55-8ed3-d84c4597e5fb ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda6.
title		Ubuntu 8.04, memtest86+ (on /dev/sda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d0687697-fe37-4b09-993e-4487512e6eb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d0687697-fe37-4b09-993e-4487512e6eb1 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04, memtest86+ (on /dev/sda8)
root		(hd0,7)
kernel		/boot/memtest86+.bin  
savedefault
boot

stephen@stephen-laptop:~$ 


```

---

### Post by forestpixie on 2008-05-29
You can see from the fstab that the partitions being used are sda12 and sda13.

I don't think that nay of the others are mounted so you can probably do it from within your booted installation with gparted. Open partition editor in system - admin menu.

It should start in sda, you can delete all the other partitions and make a new one from the unallocated space which can then be mounted as a new partition - or resize the real installation to have the space, up to you.

If you are at all unsure - post a scnsht of gparted here.

If there is data on the drive make sure you have backups, while it should be without problem you are working on partitions and there is a possibility of data loss.

---

### Post by Stephen_A on 2008-05-29
[IMG]http://i184.photobucket.com/albums/x58/Stephen_A/Gparted.png[/IMG]

I've tried removing some partitions but Gparted tells me it can't delete the partition or the 'delete' option is greyed out (inactive). How do I go about this, please?

---

### Post by forestpixie on 2008-05-29
You'll need to boot with your livecd and do it from there so that nothing is mounted.

---

### Post by Stephen_A on 2008-05-29
Still have a problem. Booted off the CD, but unable to delete /dev/sda/6; error message 'Unable to delete /dev/sda6! Please unmount any logical partitions having a number higher than 6.'

I'm unable to do this because the 'unmount' option is inactive on the menu for the partitions, or the 'unmount' option is missing altogether.

---

### Post by forestpixie on 2008-05-29
Open aterminal and turn swap off

```
sudo swapoff
```

and try again, once you've done trun swapon again

```
sudo swapon
```

---

### Post by Stephen_A on 2008-05-29
Thanks, Just found that on the forums but you beat me to it. I'll mark this 'solved' now and thanks very much for your help. There's one swap that refuses to go but I guess Ubuntu is using that.

---

### Post by forestpixie on 2008-05-29
You're welcome :)

---

