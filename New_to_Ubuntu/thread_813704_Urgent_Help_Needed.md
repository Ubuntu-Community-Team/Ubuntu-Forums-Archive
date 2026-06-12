---
title: "Urgent Help Needed"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by jerden on 2008-05-31
Hi I have been for the last 2 months triple booting Vista XP and Ubuntu Ive been  using Vista and XP mostly because Ive had to work on them so I just this minute turned on Ubuntu and installed some updates. 

Some packages couldnt be read and it asked would I like a new dconf file i think and I thought that would fix it but now to my horror it has un-installed my graphics card aswell as formatting the GRUB menu so that only Ubuntu is present I need help on what to do to get Vista back. that choice lead to the Vista and XP partitions. 

I need help please!!!

---

### Post by sam_delta on 2008-05-31
check out super grub disk, burn it and restore your grub
[www.supergrubdisk.org/](www.supergrubdisk.org/)

sam

---

### Post by meierfra. on 2008-05-31
Does /boot/grub contain any backups of menu.lst? You might use that to restore menu.lst.

Otherwise post the output of

```
sudo fdisk -l 
```

and 

```
gksudo gedit/boot/grub/menu.lst
```
(both l are lower case L)

for futher help.

---

### Post by jerden on 2008-05-31
ok for your first part it gave:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ffe8ffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       21700   174302343+   7  HPFS/NTFS
/dev/sda2           21700       24887    25601024    7  HPFS/NTFS
/dev/sda3           24888       28711    30716280    5  Extended
/dev/sda4           28712       30401    13574925    7  HPFS/NTFS
/dev/sda5           24888       25269     3068383+  83  Linux
/dev/sda6           25270       25651     3068383+  82  Linux swap / Solaris
/dev/sda7           25652       28711    24579418+  83  Linux

Disk /dev/mmcblk0: 2007 MB, 2007498752 bytes
29 heads, 28 sectors/track, 4828 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        4829     1960320+   6  FAT16
jerden@jerden-laptop:~$ 


but the second part returned nothing i dont know why because it usually does.

---

### Post by meierfra. on 2008-05-31
My bad:

```
gksudo  gedit /boot/grub/menu.lst
```

---

### Post by ugm6hr on 2008-05-31
> Does /boot/grub contain any backups of menu.lst? You might use that to restore menu.lst.

Find out by posting the output from (Little "L"):
```
ls /boot/grub/
```

---

### Post by jerden on 2008-05-31
lol here you go:

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
# kopt=root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Fix Ubuntu
root

title		Ubuntu 8.04,recovery
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=544a3a53-81ad-4692-a4b8-3645a317ab8b ro single
initrd		/boot/initrd.img-2.6.24-16-generic


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
#title		Windows Vista/Longhorn (loader)
#root		(hd0,3)
#savedefault
#makeactive
#chainloader	+1

---

### Post by meierfra. on 2008-05-31
Actually I don't need  to see "menu.lst"

Open "menu.lst"  with

```
gksudo gedit /boot/grub/menu.lst
```


Add this to the very end of the file:

title  Vista and XP
root (hd0,0)
makeactive
chainloader +1

There is small chance that this will not work, then use

title  Vista and XP
root (hd0,1)
makeactive
chainloader +1

instead

---

### Post by ugm6hr on 2008-05-31
Looks like you use the Vista bootlaoder on sda4:

Just change the following lines:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
#title Windows Vista/Longhorn (loader)
#root (hd0,3)
#savedefault
#makeactive
#chainloader +1
```

to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title Windows Vista/Longhorn (loader)
root (hd0,3)
savedefault
makeactive
chainloader +1
```

i.e. remove the hash symbols.

---

### Post by jerden on 2008-05-31
Thank you!!! It works

---

### Post by meierfra. on 2008-05-31
Time for me to go to bed. First I missed the "gedit", then I overlooked the "(hd0,3)" possibilty. But I still think, (hd0,0) was correct. Was it?

---

