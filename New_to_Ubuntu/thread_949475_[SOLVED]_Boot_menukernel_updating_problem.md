---
title: "[SOLVED] Boot menu/kernel updating problem"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Zorgoth on 2008-10-16
I am on a system with two versions of Ubuntu (32-bit and 64-bit), and 32-bit Ubuntu is not the main operating system.  Recently the kernel should have updated, but all it did was change the installation on top of the boot menu's (GRUB's) (the 64-bit's) name until I ran it and it changed back to normal, and I can't load the updated kernel.  How can I fix this?  Also, for convenience, how can I change the order of operating systems in the boot menu?

Thanks!

---

### Post by pedro_orange on 2008-10-16
You need to edit:

/boot/grub/menu.lst

As root.(or sudo)

---

### Post by Elfy on 2008-10-16
I assume that the menu list that you use then is in the 64bit install. The menu list for that won't afaik update the 32bit options as they will be outside the automagic part of the menu list.

Can you post the menu list - boot the 64bit and run this from a terminal and post the outputs

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

If you can boot any of the 32bit do so and run the cat command from there as well please.

It might be worth clarifying what you can and can't do as your post is a bit ambiguous :)

---

### Post by philinux on 2008-10-16
As above plus are you dual booting with one drive or two?

---

### Post by Zorgoth on 2008-10-16
> **philinux said:**
> As above plus are you dual booting with one drive or two?

My computer is set up kind of psychotically (on one drive).  All together, I have Windows on one partition and Ubuntu on 3 as it happens (2 32-bits and 1 64-bit, there was actually a reason), and in fact it is the second (unused and smaller) 32-bit that manages the bootloader (I had thought it was the 64-bit but was apparently wrong).  This had not been updated and was still kernel "" "" "".16 at the time when I updated the other one.  Here is what I get from the text command from here.  I will get it from the other installation as well and post it seperately.

jonathan@Zorgothia:~$ sudo fdisk -l
[sudo] password for jonathan: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe00c5762

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10485760   27  Unknown
/dev/sda2            1306       16062   118527996    7  HPFS/NTFS
/dev/sda3           16063       18493    19527007+  83  Linux
/dev/sda4           18494       30401    95651010    5  Extended
/dev/sda5           18494       19283     6345643+  82  Linux swap / Solaris
/dev/sda6           19284       26334    56637126    b  W95 FAT32
/dev/sda7           29010       30401    11181208+  83  Linux
/dev/sda8           27065       28128     8546548+  83  Linux
/dev/sda9           28129       29009     7076601   83  Linux
/dev/sda10          26335       27064     5863693+  83  Linux

Partition table entries are not in disk order
jonathan@Zorgothia:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,9)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=feb40ebe-fd05-467f-9bd5-616c88443bac ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,9)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b25f5096-b319-4c97-b4be-548d8f03d649 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b25f5096-b319-4c97-b4be-548d8f03d649 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda8.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda8)
root		(hd0,7)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Zorgoth on 2008-10-16
jonathan@Zorgothia:~$ sudo fdisk -l
[sudo] password for jonathan: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe00c5762

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10485760   27  Unknown
/dev/sda2            1306       16062   118527996    7  HPFS/NTFS
/dev/sda3           16063       18493    19527007+  83  Linux
/dev/sda4           18494       30401    95651010    5  Extended
/dev/sda5           18494       19283     6345643+  82  Linux swap / Solaris
/dev/sda6           19284       26334    56637126    b  W95 FAT32
/dev/sda7           29010       30401    11181208+  83  Linux
/dev/sda8           27065       28128     8546548+  83  Linux
/dev/sda9           28129       29009     7076601   83  Linux
/dev/sda10          26335       27064     5863693+  83  Linux

Partition table entries are not in disk order
jonathan@Zorgothia:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a8917686-b091-4a1e-be81-b325c6181695 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b25f5096-b319-4c97-b4be-548d8f03d649 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b25f5096-b319-4c97-b4be-548d8f03d649 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 8.04.1, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by damers21 on 2008-10-16
I am having a similar problem.  I recently installed the Ubuntu 8.10 beta on its own partition and the kernel update for my 8.04.1 install has not been displayed on the GRUB menu.  I will let you know if I find any solutions in the meantime.

---

### Post by Elfy on 2008-10-17
I would remove the unused ubuntu if all it is actually doing is looking after grub. Remove the partition that it resides on, at that point you will not be able to boot until grub is reinstalled. #You could then use that space to increase either of the other installs.

Personally I use [supergrub]("http://www.supergrubdisk.org/") to do my grub although you can use the [livecd]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick Start") to do the same thing.

You will be able to specify which to install it too, 64 or 32 bit - you'll know which partition is which I hope.

Please also in future use code tags around pasted text - makesit easier to scroll :)
if you are using the New Reply button then there is a # tool - highlight the text and use the tool.

If you're using quick reply then type [noparse]```
[/noparse] at the beinning and [noparse]
```[/noparse] at the end.

---

### Post by Zorgoth on 2008-10-17
Thanks!

Well I'll have to do that when I have a CD to write to.  Is it possible to put grub on my main installation from my hard disk without removing the other installation first?  I don't have access to any computer but this one (at least not one I'd be allowed to burn a CD on) and so really don't want to do something I don't know how to fix...  

I would have removed the other installation before if I knew I wouldn't do something horrible to my computer, but I don't have a CD anymore and my college would fine me if I downloaded enough to get a new live CD.

I'm something of a newb, to say the least.  So be patient with my non-comprehension...

---

### Post by Elfy on 2008-10-17
Oh yea - there's nothing to stop you reinstalling grub now with all 3 installs on there.

Use the second of the links in my last post to do that.

So you know, the supergrub download is really small it's not a full cd in fact less than 1Mb , there is also a version that works on a usb which might suit you more

[http://www.supergrubdisk.org/index.php?pid=7](http://www.supergrubdisk.org/index.php?pid=7)

---

### Post by Zorgoth on 2008-10-17
What are all the things like:
(hd0,1)

as opposed to /dev/sda# and how do I figure out what numbers to use?

---

### Post by Zorgoth on 2008-10-17
nvm about last post, i installed grub and am rebooting my computer...

---

### Post by Zorgoth on 2008-10-17
All is well now; I have my bootloader loading the right kernel.  THe only thing is that it doesn't see the unused Ubuntu, but I don't care too much about that.  Thank you!

---

### Post by Elfy on 2008-10-17
If you still need to know the relationship works so

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by Elfy on 2008-10-17
We can add the second one if you wish - rerun 
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

Please post inside code tags - end of post #8

---

