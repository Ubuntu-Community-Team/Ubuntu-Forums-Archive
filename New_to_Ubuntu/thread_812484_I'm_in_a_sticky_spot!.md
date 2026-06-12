---
title: "I'm in a sticky spot!"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by fishman78 on 2008-05-29
Howdy!

  So I decided to take the plunge and try unbuntu, but the GRUB loader is not working at all.  When I boot up I get Grub loading error 21.... BIOS detects all disks.  Now, I have two disks running a raid and one stand alone that ubuntu went on.  Does the raid pose a problem?  If I turn off the raid controller I can boot into ubuntu but ofcorse windows is nowhere on the list.  Is there a fix for this?  Did i do something wrong?  I tried loading grub on both the raid and the stand alone.  Any help would be greatly appreciated.  Thanks!

Kurt

---

### Post by tamoneya on 2008-05-29
RAID shouldnt pose a problem if GRUB is correctly configured.  Post the file: /boot/geub/menu.lst and the output of ```
sudo fdisk -l
```That will allow us to become familiar with your computer and enable us to configure grub correctly.

---

### Post by dhughes on 2008-05-29
> **tamoneya said:**
> RAID shouldnt pose a problem if GRUB is correctly configured.  Post the file: /boot/geub/menu.lst and the output of ```
sudo fdisk -l
```That will allow us to become familiar with your computer and enable us to configure grub correctly.


 Small typo, I believe you meant:

  /boot/**grub**/menu.lst

---

### Post by fishman78 on 2008-05-30
Here is the output for sudo fdisk -l: (please note that the raid is off as that's the only way I can get into ubuntu.  Can't get into windows)

ubuntu@ubuntu-PC:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9468cac3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23891   191902720    7  HPFS/NTFS
/dev/sda2           23891       36640   102400000    7  HPFS/NTFS
/dev/sda3           36640       60802   194085888    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000170c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29173   234332091   83  Linux
/dev/sdc2           29174       30401     9863910    5  Extended
/dev/sdc5           29174       30401     9863878+  82  Linux swap / Solaris
ubuntu@ubuntu-PC:~$

---

### Post by fishman78 on 2008-05-30
And here is a copy of the grub info menu.lst:

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
# kopt=root=UUID=de3bfba5-1598-46d8-882d-de1f51a2e802 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=de3bfba5-1598-46d8-882d-de1f51a2e802 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=de3bfba5-1598-46d8-882d-de1f51a2e802 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=de3bfba5-1598-46d8-882d-de1f51a2e802 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=de3bfba5-1598-46d8-882d-de1f51a2e802 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Thanks for your help!!  I really appreciate it!!

Kurt

---

