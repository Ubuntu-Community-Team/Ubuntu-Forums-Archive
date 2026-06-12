---
title: "grub prob"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by nnjond on 2008-05-14
Hi, can anyone help me?

I have dug a dual-boot deep hole. But I think I can get out if I can uninstall grub from the grub prompt. Is that posible?

thanks

---

### Post by kirios on 2008-05-14
It may be easier to fix the "deep hole" instead. Details?

> **nnjond said:**
> Hi, can anyone help me?

I have dug a dual-boot deep hole. But I think I can get out if I can uninstall grub from the grub prompt. Is that posible?

thanks

---

### Post by nnjond on 2008-05-14
Thanx for your interest, but I'mm not sure what i've done except install a second Hardy on my 2nd physical (ancillary) disc where all my data is. this disc no longer shows up in Win 2000 or Hardy

---

### Post by Paqman on 2008-05-14
> **nnjond said:**
> Thanx for your interest, but I'mm not sure what i've done except install a second Hardy on my 2nd physical (ancillary) disc where all my data is. this disc no longer shows up in Win 2000 or Hardy

That's not going to be solvable by reinstalling Grub. All Grub does is tell the computer which OS to boot, and where to find it.

Can you please post the output of:
```

sudo fdisk -l

```

---

### Post by nnjond on 2008-05-14
Incomplete post

---

### Post by nnjond on 2008-05-14
nnjond@nnjond-desktop:~$ sudo fdisk -l
[sudo] password for nnjond: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa459283

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3666    29439112    7  HPFS/NTFS
/dev/sda2            3666        8246    36796851+   f  W95 Ext'd (LBA)
/dev/sda3            8247       10011    14177362+  83  Linux
/dev/sda5            3666        3927     2104483+  82  Linux swap / Solaris
/dev/sda6            3928        4189     2104483+  82  Linux swap / Solaris
/dev/sda7            4190        6536    18852246   83  Linux
/dev/sda8            6537        8162    13060813+  83  Linux
/dev/sda9            8163        8246      674698+  82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31ac70c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
nnjond@nnjond-desktop:~$

---

### Post by kirios on 2008-05-14
Some more info required. Please post the contents of **/boot/grub/menu.lst** and **/etc/fstab**.

> **nnjond said:**
> nnjond@nnjond-desktop:~$ sudo fdisk -l
[sudo] password for nnjond: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa459283

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3666    29439112    7  HPFS/NTFS
/dev/sda2            3666        8246    36796851+   f  W95 Ext'd (LBA)
/dev/sda3            8247       10011    14177362+  83  Linux
/dev/sda5            3666        3927     2104483+  82  Linux swap / Solaris
/dev/sda6            3928        4189     2104483+  82  Linux swap / Solaris
/dev/sda7            4190        6536    18852246   83  Linux
/dev/sda8            6537        8162    13060813+  83  Linux
/dev/sda9            8163        8246      674698+  82  Linux swap / Solaris
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31ac70c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       19457   156280320    f  W95 Ext'd (LBA)
nnjond@nnjond-desktop:~$

---

### Post by nnjond on 2008-05-14
Thank again. What's the best way to do that?

Have figured it out

---

### Post by nnjond on 2008-05-14
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
color cyan/blue white/blue

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
# kopt=root=UUID=95f8506b-2449-4699-910a-b95e06bed52c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=quiet splash vga=791

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=95f8506b-2449-4699-910a-b95e06bed52c ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=95f8506b-2449-4699-910a-b95e06bed52c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=95f8506b-2449-4699-910a-b95e06bed52c ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=95f8506b-2449-4699-910a-b95e06bed52c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		openSUSE 10.3 (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_HDS728080PLAT20_PFD219EJR27NBE-part7 vga=0x314 resume=/dev/sda6 splash=silent showopts 
initrd		/boot/initrd-2.6.22.5-31-default
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Failsafe -- openSUSE 10.3 (on /dev/sda7)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_HDS728080PLAT20_PFD219EJR27NBE-part7 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd-2.6.22.5-31-default
savedefault
boot


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=95f8506b-2449-4699-910a-b95e06bed52c / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda9 :
UUID=b44fda0a-75a3-4ec9-a521-0f3b276be31c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

---

### Post by kirios on 2008-05-14
**fdisk -l** shows sdb as a single non-Linux partition, so your second install of Hardy may have been on sda3 where you seem to have initially installed Hardy. That may explain the 2 sets of entries for Ubuntu in your **menu.lst**. But there's also an entry for Windows in **menu.lst**, so you should be able to dual-boot. So the problem is "*my 2nd physical (ancillary) disc where all my data is. this disc no longer shows up in Win 2000 or Hardy*"? Is that a FAT32 partition? 

```
sudo mkdir /mnt/mydata
sudo mount /dev/sdb1 /mnt/mydata
sudo chmod -R o+rwx /mnt/mydata
```
Try to navigate to */mnt/mydata* in the file manager.

> **nnjond said:**
> Thanx for your interest, but I'mm not sure what i've done except install a second Hardy on my 2nd physical (ancillary) disc where all my data is. this disc no longer shows up in Win 2000 or Hardy

---

### Post by nnjond on 2008-05-14
It seems i was wrong as to where my 2nd Hardy was installed. My ancillary disk is Fat 32 with all my data on it, but it doesnt show up in any OS. Thats the main Prob. also how to get rid of the 2nd Hardy. thanks

NB I also have opensuse on my Primary disk (sda ?) will Post some more.

---

### Post by kirios on 2008-05-14
Try mounting sdb1 at the command line.

Btw Suse is on sda7. 

> **nnjond said:**
> It seems i was wrong as to where my 2nd Hardy was installed. My ancillary disk is Fat 32 with all my data on it, but it doesnt show up in any OS. Thats the main Prob. also how to get rid of the 2nd Hardy. thanks

NB I also have opensuse on my Primary disk (sda ?) will Post some more.

---

### Post by nnjond on 2008-05-14
nnjond@nnjond-desktop:~$ sudo mkdir /mnt/mydata
mkdir: cannot create directory `/mnt/mydata': File exists
nnjond@nnjond-desktop:~$ sudo mount /dev/sdb1 /mnt/mydata
mount: you must specify the filesystem type
nnjond@nnjond-desktop:~$ sudo chmod -R o+rwx /mnt/mydata
nnjond@nnjond-desktop:~$

---

### Post by nnjond on 2008-05-14
mistake

---

### Post by nnjond on 2008-05-14
nnjond@nnjond-desktop:~$ mont sdb1
bash: mont: command not found
nnjond@nnjond-desktop:~$

---

### Post by Paqman on 2008-05-14
Your other Hardy install is on sda8. If you don't need it you can just delete that partition in Gparted. You also don't need three swap partitions. Any number of Linux installs can share one swap (unless you use hibernate) 

It looks to me like you've created an empty extended partition on sdb, overwriting your FAT32 data partition.

---

### Post by nnjond on 2008-05-14
Thanks for all yor help. I take it you think the data is lost. Does the sleep button on my keyboard mean hibernate? Is Gparted the equivilent of Gnome Partion Editor?

---

