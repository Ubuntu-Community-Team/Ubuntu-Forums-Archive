---
title: "vista drive not recognized, vista not booting"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by NAWSE on 2008-12-01
my friend used to have only vista. i installed ubuntu for him and after some time he needed some space so while he was in vista he formatted the ubuntu ext3 drive(and i, like a dumbo, let him do that). so he lost ubuntu and the grub. so we installed ubuntu once again with the hope of dualbooting, but with no luck. the 53gb vista drive is not recognized, and of course vista didnt show up at all. but i was able to see the vista drive in gparted and when i tried to mount it i got
[B]
Could not mount /dev/sda1 on /media/sda1
mount:you must specify the file system type[/B]

i looked at another such thread and edited the /boot/grub/menu.lst, and i got an option "Vista" at boot but if i press it i get 

**Error 21: Selected disk does not exist**

i'm posting outputs of various commands here 

_**[COLOR="Red"]sudo fdisk -l[/COLOR]**_

[B]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6125db67

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6853 55040661 7 HPFS/NTFS
/dev/sda2 6853 18601 94370485 f W95 Ext'd (LBA)
/dev/sda3 18602 19457 6875820 7 HPFS/NTFS
/dev/sda5 6853 10769 31456256 7 HPFS/NTFS
/dev/sda6 10770 10831 497983+ 82 Linux swap / Solaris
/dev/sda7 10832 11804 7815591 83 Linux
/dev/sda8 11805 18601 54596871 b W95 FAT32


[/B]

[COLOR="Red"]**_sudo /boot/grub/menu.lst_**[/COLOR]

[B]# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title Vista
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1

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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bed0d1dd-53a2-46b5-ad9b-1f40114a6197 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=bed0d1dd-53a2-46b5-ad9b-1f40114a6197 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=bed0d1dd-53a2-46b5-ad9b-1f40114a6197 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST[/B]

[COLOR="Red"][B][U]sudo grub
[/U][/B][/COLOR]
[B]>grub 
geometry (hd0)
drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sda
Partition num: 0, Filesystem type unknown, partition type 0x7
Partition num: 2, Filesystem type unknown, partition type 0x7
Partition num: 4, Filesystem type unknown, partition type 0x7
Partition num: 5, Filesystem type unknown, partition type 0x82
Partition num: 6, Filesystem type is ext2fs, partition type 0x83
Partition num: 7, Filesystem type is fat, partition type 0xb

>grub
geometry (hd1)
Error 21: Selected disk does not exist[/B]

[COLOR="Red"]**_sudo mount /dev/sda1_**[/COLOR]
[B]Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
[/B]

i feel so sorry for him, he doesn't have the vista backup dvd or the recovery dvd. :(

---

### Post by nhasian on 2008-12-01
Have you tried fixing it with the super grub disk?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by caljohnsmith on 2008-12-01
According to the fdisk command, your sda drive is 160 GB, and is that your Vista drive? You said the Vista drive was 53 GB. And when you say you got an option for Vista at boot, do you get the Grub menu on start up? Because before that you say you had no luck installing Ubuntu, so I'm a bit confused.

If your friend just wants to get Vista back and not use Ubuntu, then how about having him boot his Vista Install CD, go to the command line, and run:
```
bootrec /fixmbr
bootrec /fixboot
chkdsk /r
```
And have him run the chkdsk command as many times as necessary until it reports no errors. Since you couldn't mount sda1 and it complained that "you must specify the file system", I'm guessing that at some point you might have accidentally installed Grub to the boot sector of the Vista partition. But doing the "bootrec /fixboot" above should fix that. If your friend doesn't have a Vista Install CD, he can instead download and use a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let me know how it goes.

---

