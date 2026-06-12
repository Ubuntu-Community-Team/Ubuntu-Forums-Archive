---
title: "Re-partitioned Swap &amp; now won't boot"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by bjstabio on 2008-06-29
Using GParted, I re-partitioned my swap file, which I thought was too large at 6 GB.  Now Ubuntu won't boot.  All I get is a blank screen with a blinking cursor.  I have looked at menu.lst & it looks okay to me, but that doesn't mean much. I truly am a beginner.  Any help would be greatly appreciated.

---

### Post by lisati on 2008-06-29
Did you leave your swap partition formatted for swapping?

---

### Post by drs305 on 2008-06-29
Please post these if you can and we can see where the problem lies:
```
cat /etc/fstab && sudo blkid && sudo fdisk -l

```

---

### Post by bjstabio on 2008-06-29
> **drs305 said:**
> Please post these if you can and we can see where the problem lies:
```
cat /etc/fstab && sudo blkid && sudo fdisk -l

```

earmusic@earmusic-host:~$ cat /etc/fstab && sudo blkid && sudo fdisk -l
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=94e3627f-fed0-4b77-ae28-54336af4f1b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=68159b9a-c8b0-4ac3-803c-4b3b6ef41f1c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
[sudo] password for earmusic: 
/dev/sda1: UUID="94e3627f-fed0-4b77-ae28-54336af4f1b7" TYPE="ext3" 
/dev/sda5: TYPE="swap" LABEL="ID_FS_USAGE=oth" UUID="93dec0d6-91cc-4f97-b8b7-66c77361516d" 
/dev/sda6: UUID="4e13343a-4384-4882-9be5-93d1118fb071" TYPE="ext2" 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001d58c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6233    50066541   83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda3            6234       12447    49913955   83  Linux
/dev/sda4           12448       18662    49921987+  83  Linux
/dev/sda5           18663       19064     3229033+  82  Linux swap / Solaris
/dev/sda6           19065       19457     3156741   83  Linux

Partition table entries are not in disk order

---

### Post by drs305 on 2008-06-29
> **bjstabio said:**
> 

# /dev/sda5
UUID=68159b9a-c8b0-4ac3-803c-4b3b6ef41f1c none            swap    sw              0       0

/dev/sda5: TYPE="swap" LABEL="ID_FS_USAGE=oth" UUID="93dec0d6-91cc-4f97-b8b7-66c77361516d" 


First, the swap uuid is not correct. It was changed when you repartitioned/reformatted your disk. 
Change fstab so the /dev/sda5 swap partition matches blkid:

```

sudo cp etc/fstab /etc/fstab-bak
gksudo gedit /etc/fstab
[CODE]

[CODE]# /dev/sda5
UUID=93dec0d6-91cc-4f97-b8b7-66c77361516d none            swap    sw              0       0
```

Also, your sda6 partition is not listed in fstab...


Then if you are still having problems post your menu.lst

---

### Post by bjstabio on 2008-06-29
> **drs305 said:**
> First, the swap uuid is not correct. It was changed when you repartitioned/reformatted your disk. 
Change fstab so the /dev/sda5 swap partition matches blkid:

```

sudo cp etc/fstab /etc/fstab-bak
gksudo gedit /etc/fstab
[CODE]

[CODE]# /dev/sda5
UUID=93dec0d6-91cc-4f97-b8b7-66c77361516d none            swap    sw              0       0
```

Also, your sda6 partition is not listed in fstab...


Then if you are still having problems post your menu.lst

Still won't boot but I truly appreciate all the help.  Thanks!  Here is my menu.lst:  I didn't do anything with sda6 not being listed in fstab; don't know what to do or if it makes any difference.

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
# kopt=root=UUID=94e3627f-fed0-4b77-ae28-54336af4f1b7 ro

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

title		eAR OS, kernel 2.6.24-19-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=94e3627f-fed0-4b77-ae28-54336af4f1b7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-rt
quiet

title		eAR OS, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=94e3627f-fed0-4b77-ae28-54336af4f1b7 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		eAR OS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by drs305 on 2008-06-29
I don't see any big errors in menu.lst. You might want to confirm you are running kernel 19rt with this command:
```
uname -r
```

To add /dev/sda6 to fstab:
First make a mount point and make yourself the owner (I'll use **sda6** but call it what you want):
```

sudo mkdir /media/**sda6**
sudo chown -R **username:username** /media/**sda6**

```

Then add this line to fstab:
```

# /dev/sda6
UUID="4e13343a-4384-4882-9be5-93d1118fb071" /media/**sda6** ext2 defaults 0 2

```

---

### Post by bjstabio on 2008-06-29
> **drs305 said:**
> I don't see any big errors in menu.lst. You might want to confirm you are running kernel 19rt with this command:
```
uname -r
```

To add /dev/sda6 to fstab:
First make a mount point and make yourself the owner (I'll use **sda6** but call it what you want):
```

sudo mkdir /media/**sda6**
sudo chown -R **username:username** /media/**sda6**

```

Then add this line to fstab:
```

# /dev/sda6
UUID="4e13343a-4384-4882-9be5-93d1118fb071" /media/**sda6** ext2 defaults 0 2

```

earmusic@earmusic-host:~$ uname -r
2.6.24-19-rt

Thanks again for the help.  I'll just reinstall the OS as I won't be losing anything important.  I thought by trying to fix the problem I would learn something & I have, thanks to you.

---

