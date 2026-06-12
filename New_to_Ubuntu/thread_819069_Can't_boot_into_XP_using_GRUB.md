---
title: "Can't boot into XP using GRUB"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by metalhead on 2008-06-05
I've tried to avoid posting my problem, but I've spent most of today reading through many posts and getting nowhere. Here's the problem: I installed Ubuntu 8.04 yesterday on a IDE 80GB HD and had GRUB install on my Windows XP SATA hard drives (that's probably where I screwed up) and cannot load Windows XP (I did once, but haven't been able to do it again). I say hard drives because I have two Western Digital 150GB Raptors in RAID 0. Before I installed 8.04 I formatted the IDE drive (removing 7.10) to install a fresh install of 8.04. I have the Raptors as my first drive to boot, and the IDE as my second. I've switched the HD order back and forth, but no luck. I've tried removing GRUB from the Raptors, FIXBMR, FIXBOOT, and copying NTLDR and NTDETECT.COM to the Raptors. I've tried disconnecting the IDE drive and boot, but no luck even after trying to fix the MBR. I've edited the grub menu.lst using various posts, but only one time did it work (and I backed up my important files while I could). Re-installing XP is not a option. I currently get the ERROR 17, but have read through the posts on it and still can't XP to load. Below is a fdisk of my system and below that is the grub menu list:


metalhead@metalhead-desktop:~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x3c068427 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        9327    74919096   83  Linux 
/dev/sda2            9328        9729     3229065    5  Extended 
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris 

Disk /dev/sdb: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x10bff210 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS 

Disk /dev/sdc: 150.0 GB, 150039945216 bytes 
255 heads, 63 sectors/track, 18241 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x28132812 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *           1       36482   293041633+   7  HPFS/NTFS 

Disk /dev/sdd: 150.0 GB, 150039945216 bytes 
255 heads, 63 sectors/track, 18241 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00000048 

Disk /dev/sdd doesn't contain a valid partition table 

Disk /dev/sde: 300.0 GB, 300069052416 bytes 
255 heads, 63 sectors/track, 36481 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00015b3a 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sde1               2       36481   293025600    f  W95 Ext'd (LBA) 
/dev/sde5               2       36481   293025568+   7  HPFS/NTFS 

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x44fdfe06 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdf1   *           1      121601   976760001    7  HPFS/NTFS 
metalhead@metalhead-desktop:~$ 


Here's my /boot/grub/menu.lst:

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
timeout		15

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
# title		Windows Windows XP Professional
# root		(hd3,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd1,0)
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
# kopt=root=UUID=612540ba-5cf3-43b5-8e59-bfc0766f0d05 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd3,0)
# groot=(hd3,0)

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=612540ba-5cf3-43b5-8e59-bfc0766f0d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=612540ba-5cf3-43b5-8e59-bfc0766f0d05 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1

title		Microsoft Windows XP Professional
map (hd3) (hd1)
map (hd1) (hd3)
rootnoverify (hd3,0)
savedefault
chainloader	+1


Can someone please help? I've been dabbling in Linux off and on for about 3 years and have found Ubuntu the easiest, but I find the code thing a bit hard to understand. I'm getting better at the code thing by after using the terminal, but I've been stuck in Windows too long so don't geek me out too bad. I build my own computers and for friends and my son's school, so I'm not new to computers, just not an expert on Linux. I hope I've posted enough information for someone to decipher to fix my problem. Thanks!  [http://ubuntuforums.org/images/icons/icon9.gif](http://ubuntuforums.org/images/icons/icon9.gif)

---

### Post by Paqman on 2008-06-05
Which partition is your Windows install on? You've got NTFS partitions on sdb1, sdc1, sde5 and sdf1. You need to point Grub to the right one.

Grub numbers from zero. So sdb1 (drive 2, partition 1) is hd1,0 while sde5 would be hd4,4.
So what you need to do is edit the Windows entry at the very bottom of your menu.lst so that it looks like:
> 
title Microsoft Windows XP Professional
rootnoverify (hd**drive**,**partition**)
makeactive
chainloader +1


---

### Post by Xiong Chiamiov on 2008-06-05
[quote=metalhead]
I've tried to avoid posting my problem, but I've spent most of today reading through many posts and getting nowhere.
[/quote]
Thank you for searching.  Don't feel bad about asking us problems, as long as you're willing to do some work too.

Paqman's got you covered, but I've found that [SuperGrubDisk]("http://supergrubdisk.org") is pretty much amazing.  It guides you through creating a new GRUB menu all nice and easy, and with lots of smiley faces!

---

### Post by metalhead on 2008-06-05
I have two external HD's, and one other internal SATA drive - 160GB. Windows XP is installed on SDE1 and 5: 

Disk /dev/sde: 300.0 GB, 300069052416 bytes 
255 heads, 63 sectors/track, 36481 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x00015b3a 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sde1               2       36481   293025600    f  W95 Ext'd (LBA) 
/dev/sde5               2       36481   293025568+   7  HPFS/NTFS 

 I also tried the SuperGrub Disk and it wasn't any help, but I did learn a few things from it. I've even read some of the Grub Page and mapping doesn't seem to work either, but it did the one and only time I booted into XP. I haven't been able to replicate it since. I did a few other changes on the menu.lst and I'm about to try it out. Thanks for any suggestions.

---

### Post by metalhead on 2008-06-05
Still a no go. My brain is mush after beating myself with this today and it's time to call it a night and give some of you gurus a chance to figure out why I can't boot into XP. My last resort would to use my IMAGE of XP to restore, but I would rather not if there's a fix for this weird problem. Thanks!:popcorn:

---

### Post by Paqman on 2008-06-05
Sde5 looks like the one you want then. Sde1 is an extended partition containing sde5.

What does your menu.lst look like now?

---

### Post by Xiong Chiamiov on 2008-06-05
I believe one of these two should work:
```

title           Windows NT/2000/XP (loader)
root            (hd4,0)
makeactive
chainloader     +1

```
```

title           Windows NT/2000/XP (loader)
root            (hd4,4)
makeactive
chainloader     +1

```

Tell us how it goes.  There's also an option somewhere in SGD (the navigation on that things confuses the hell out of me) to be able to choose a partition to boot directly from.  If you can find that, then you can check and make sure you've got the right partition that's bootable.

---

### Post by metalhead on 2008-06-05
Well, I'm now back in XP, but the (hd4,0) wasn't the answer. I got an ERROR 21: SELECTED DISK DOES NOT EXIST. I then edited the command string to (hd3,0) which had worked the one time before and it booted into XP. I will go back into Ubuntu and change my menu.lst to reflect this and hope it works. One other question: if I get this to work how do I get XP to be the default OS to boot when GRUB loads? XP is my main OS, but I like to play around in Ubuntu. I'll let you all know what happens as I'm still learning. Thanks! :eek:

---

### Post by metalhead on 2008-06-05
Success! I changed the (hd4,0) to (hd3,0) in the menu,lst and grub booted XP with no problems. :biggrin: Now if I can get XP as my default boot OS in GRUB then I'll be set. I now consider this issue resolved. Thanks for your help!

---

