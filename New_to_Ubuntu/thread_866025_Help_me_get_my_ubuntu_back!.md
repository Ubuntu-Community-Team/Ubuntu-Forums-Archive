---
title: "Help me get my ubuntu back!"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by appi2012 on 2008-07-21
Basically, I installed ubuntu alongside windows, in a dual boot environment. However, because of a Recovery partition, windows couldn't boot. So I tried reinstalling windows, and used: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to try to get grub back. I used the first guide on the page, and it seemed to work. I rebooted, and got to the grub screen. However, none of the options worked. Next, I used Super Grub disk to try to boot linux or windows. However, with that, I could only boot my windows partition. Also, another strange thing I found was that my ubuntu partition was listed as UNKNOWN type. However, after booting into my kubuntu-kde4 live cd (I had ubuntu, but I wanted to try kde4), I could mount the partition labeled ext3 volume, and was able to see all my files. Now, I tried doing the guides again, but whenever I do 
```
sudo grub
``` and
```
find /boot/grub/stage1
``` It says:
```
Error 15: File not found
```
This is strange, because through dolphin file manager, I can see the file called stage1 in /boot/grub/
After this, I tried the next guide on the page. Doing ```
sudo grub-install --root-directory=/mnt/root /dev/sda
``` returned:
```
The file /mnt/root/boot/grub/stage1 not read correctly.
```

I am thoroughly perplexed. :confused: Can someone tell me what to do? How can I fix the stage1 file? I don't want to reinstall ubuntu, but I will if I don't have any more options.

btw, i'm posting this from my kubuntu liveCD

Thanks in advance!

---

### Post by appi2012 on 2008-07-21
Anyone?

---

### Post by rockerphil on 2008-07-21
my suggestion would be this. if you've got the Windows recovery disk i'd simply get my hands on a copy of the Gparted Live CD and completely get rid of all partitions and start over, but since you say it was originally caused by a recovery partition i'm guessing you don't have the Windows recovery CD. so i'd contact the manufactorer of your computer, they can't deny you a physical recovery disk, they're just trying to be cheap by creating a recovery partition so they don't have to create a physical CD. but since you're dual booting with Linux what if somthing goes wrong and that partition is deleted? yo'll be forced to go straight Linux, but yea, that's my advice since it was origianlly caused by the recovery partition

---

### Post by dracayr on 2008-07-21
the stage1 file and its variants (for example e2fs_stage1.5) are needed to mount a filesystem in grub. Mounting the fs in the first place is not working. Try running 
```
fsck *root partition*
```. also please post the output of fdisk -l

dracayr

---

### Post by bumanie on 2008-07-21
> However, because of a Recovery partition, windows couldn't boot. So I tried reinstalling windows, and used: Can you expalin how the recovery partition prevented windows from booting? I assume with a recovery partition, you have vista - correct? 
Grub error 15 has something to do with grub not being able to find the correct linux kernel image to boot from. Boot live ubuntu cd and post output of > sudo fdisk -lAlso go to Places --> Computer --> file system. Then find boot directory, open it, then open grub directory and find menu.lst and copy and paste it here. Also look [here]("http://users.bigpond.net.au/hermanzone/p15.htm"), about 2/3 down the page there is a list of grub errors and likely fixes.

---

### Post by appi2012 on 2008-07-21
Another problem. I mounted my ubuntu disk using this command:
```
sudo mount -t ext3 /dev/sda2 /mnt/root
```

However, when trying to do fsck, there is a warning that says:
```
/dev/sda2 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?
```

However, when I try to unmount it through dolphin, it says
```
org.freedesktop.Hal.Device.Volume.NotMountedByHal:
Device to unmount is not in /media/.hal-mtab so it is not mounted by hal
```

and when I type:
```
sudo umount /mnt/root
```
it says
```
umount: /mnt/root: device is busy
umount: /mnt/root: device is busy
```

Any Ideas?

Here's my fdisk -l:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6889    55335861    7  HPFS/NTFS
/dev/sda2   *        6890       18340    91980157+  93  Amoeba
/dev/sda3           18341       18462      979965    5  Extended
/dev/sda4           18463       19457     7990920   1c  Hidden W95 FAT32 (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           18341       18462      979933+  82  Linux swap / Solaris
```
That Amoeba is my ubuntu partition. 
I have xp, not vista.

here's my menu.lst:
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,2)/boot/grub/splashimages/AquaDreams4bydeadpxl.xpm.gz

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
# kopt=root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro

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
# defoptions=quiet splash vga=792

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
# howmany=2

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=d0db05f8-84cc-44ea-b3cd-6a3324776898 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, memtest86+
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
title		Microsoft Windows XP Home Edition
unhide		(hd0,0)
hide		(hd0,1)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
unhide		(hd0,1)
hide		(hd0,0)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

