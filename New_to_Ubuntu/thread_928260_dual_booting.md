---
title: "dual booting"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by seyiisq on 2008-09-23
I am dual booting btw windows and ubuntu but now i get into my windows i don't even have the menu options
 
below are useful info.

afetr doing   'sudo fdisk -l' i got

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42d242d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4924    39551998+  83  Linux
/dev/sda2            4925       19452   116696160   82  Linux swap / Solaris

my menu.lst is as below

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
# kopt=root=UUID=8ce639cd-d17b-4c4c-844e-23d1a349c2ef ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ce639cd-d17b-4c4c-844e-23d1a349c2ef ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ce639cd-d17b-4c4c-844e-23d1a349c2ef ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

pls can someone help

---

### Post by jimmy the saint on 2008-09-23
I hate to tell you this, but it looks like you don't have a windows partition.  Did you install Ubuntu AFTER Windows and select "use entire disk?"  If you did, you installed Ubuntu OVER your windows install, essentially wiping it out.

---

### Post by seyiisq on 2008-09-23
i installed ubuntu after windows but i did not choose the entire disk. i only use 44G for ubuntu. pls see below

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              38G  2.4G   34G   7% /
varrun                501M  116K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   40K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M   38M  464M   8% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon       38G  2.4G   34G   7% /home/seyi/.gvfs

---

### Post by lisati on 2008-09-23
I couldn't see anything that looked like a Windows partition either. How did you assign the 44Gb for Ubuntu? Was it from the installer, or was it from gparted?

---

### Post by kansasnoob on 2008-09-23
This:

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 4924 39551998+ 83 Linux
/dev/sda2 4925 19452 116696160 82 Linux swap / Solaris

says that you have no Windows partition.

Look at mine:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9729    47431912+   5  Extended
/dev/sda5            3825        6934    24981043+  83  Linux
/dev/sda6            6935        7175     1935801   82  Linux swap / Solaris
/dev/sda7            7176        9617    19615333+  83  Linux
/dev/sda8            9618        9729      899608+  82  Linux swap / Solaris


Win XP on sda1, Ubuntu 8.04 on sda5, 8.10 on sda7.

It appears that you wiped out Windows.

You could also install gparted:

```
sudo apt-get install gparted
```

Then go to System > Administration > Partition Editor and have a look, but I'll bet you only show the Linux partitions.

---

### Post by bumanie on 2008-09-23
Windows is definitely gone. If you had important information on it, it may be possible to retrieve it by using testdisk from [here]("http://www.cgsecurity.org/wiki/TestDisk")Read the documentation first. Or you could try ntfsprogs and use ntfsundelelte.

---

### Post by hsienloong on 2008-09-23
Reinstall>>>take care of partitions>>>use LILO boot

---

