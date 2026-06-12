---
title: "ubuntu - upslash"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by ibizatunes on 2008-10-26
My upslash is always going into text mode not graphical mode
The ubuntu log comes up then it drops into text

 how do i fix this?

---

### Post by Elfy on 2008-10-26
Couple of things could cause this that I know of - check your menu list - does the kernel line have quiet splash at the end 

```
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro [COLOR="Red"]quiet splash[/COLOR]
cat /boot/grub/menu.lst
```

If you have been changing partitions, run ```
sudo blkid
``` the UUID for the swap needs to be the same in ```
cat /etc/initramfs-tools/conf.d/resume
``` if thta file exists.

If the UUID in /etc/initramfs-tools is different then change it to suit the one reported in blkid with you editor and run 

```
sudo update-initramfs -u
```

---

### Post by PocketDog on 2008-10-26
Also change the relevant Swap's UUID entry in your fstab

---

### Post by ibizatunes on 2008-10-26
I try upgrading to ibex but that didnt help, i had this problem in 8.04

/boot/vmlinuz-2.6.27-7-generic root=UUID=b43ae0ac-40a4-4e2c-8280-3d1c1688652a ro splash 


===
sudo blkid
/dev/sda1: UUID="36C03B1FC03AE531" TYPE="ntfs" LABEL="Windows XP" 
/dev/sda6: TYPE="swap" UUID="ebf15c22-e226-43e2-a12c-885991d7f67c" 
/dev/sdb1: LABEL="M-\OM-r^GvM-7hIM-sfM-]" UUID="2C1C-BE44" TYPE="vfat" 
/dev/sdb6: TYPE="swap" UUID="ebf15c22-e226-43e2-a12c-885991d7f67c" 
/dev/sda5: UUID="b43ae0ac-40a4-4e2c-8280-3d1c1688652a" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdc1: UUID="2C1C-BE44" TYPE="vfat" LABEL="M-\OM-r^GvM-7hIM-sfM-]" 
/dev/sdc5: TYPE="swap" UUID="ee156608-9fef-4fa2-98c2-e4e59d9a994f" 


===

cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=94680938-d14a-4779-a197-4e1ec410b382

---

### Post by Elfy on 2008-10-26
They are different, as pocketdog says likely that it's wrong in fstab too. 

Edit the files after backing up 


```
sudo cp /etc/fstab /etc/fstab.2610
cp /boot/grub/menu.lst /boot/grub/menu.lst.2610
cp /etc/initramfs-tools/conf.d/resume /etc/initramfs-tools/conf.d/resume.2610
```

Edit the files

```
gksudo gedit /boot/grub/menu.lst
```
change end of kernel line to [quote]ro quiet splash[/code]

```
gksudo /etc/fstab
```

Look for line which relates to the swap partition - _it could be either sdb6 or sdc5_ - for some reason you have 2 and make sure that the UUID line is replaced by the correct UUID from your blkid results above

Now the UUID for whichever swap you are actually using in fstab needs to be shown in the resume file - 

```
gksudo gedit  /etc/initramfs-tools/conf.d/resume
```

Once that file has been edited run

```
sudo update-initramfs -u
```

If you have problems come back, if fstab and swap are confusing you post

```
cat /etc/fstab
```

---

### Post by ibizatunes on 2008-10-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
RESUME=UUID=94680938-d14a-4779-a197-4e1ec410b382 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
RESUME=UUID=94680938-d14a-4779-a197-4e1ec410b382e            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
elliott@elliott-desktop:~$

---

### Post by ibizatunes on 2008-10-26
i think the swap fails to load now, i have defo done something wrong

---

### Post by Elfy on 2008-10-26
Yes for some reason you added the swap uuid to your fstab for your root partition and also added stuff you shouldn't have  - please post result of this

```
cat /etc/fstab.2610
cat /etc/initramfs-tools/conf.d/resume
cat /boot/grub/menu.lst
```

---

### Post by ibizatunes on 2008-10-26
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b43ae0ac-40a4-4e2c-8280-3d1c1688652a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=94680938-d14a-4779-a197-4e1ec410b382 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=====

cat /etc/initramfs-tools/conf.d/resume

===

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
# kopt=root=UUID=b43ae0ac-40a4-4e2c-8280-3d1c1688652a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
# defoptions=quiet splash xforcevesa

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b43ae0ac-40a4-4e2c-8280-3d1c1688652a ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=b43ae0ac-40a4-4e2c-8280-3d1c1688652a ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Elfy on 2008-10-26
Please use code tags in future -  # button in New Reply tool bar or [noparse]```
 at beginning and 
``` at end of pasted output[/noparse] - makes it easier to read thread.

Ok we'll replace fstab with backup then open it for editing

```
sudo cp /etc/fstab.2610 /etc/fstab
gksudo /etc/fstab
```

Note changes in red - make only that change, the first line that read 
RESUME=UUID=94680938-d14a-4779-a197-4e1ec410b382 should be different in fstab now due to the backup

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
RESUME=UUID=94680938-d14a-4779-a197-4e1ec410b382 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
[COLOR="Red"]UUID=ebf15c22-e226-43e2-a12c-885991d7f67c swap sw 0 0[/COLOR]
/dev/hda /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/hdb /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
elliott@elliott-desktop:~$

Save, close and reboot - check all mounts ok and that you get quiet and splash at start

---

### Post by ibizatunes on 2008-10-26
thanks that fixed it!!!

---

### Post by Elfy on 2008-10-26
cool - if all is done can you mark thread solved please

---

