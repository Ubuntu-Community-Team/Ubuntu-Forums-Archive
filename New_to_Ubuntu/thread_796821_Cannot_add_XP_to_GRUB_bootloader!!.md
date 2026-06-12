---
title: "Cannot add XP to GRUB bootloader!!"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by samknex on 2008-05-16
OK here is something tricky
I am having a problem with dual booting UBuntu 8.04 and XP. I am trying to add XP to GRUB bootloader. I sure hope that somebody notices this. here is my sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00bbbca2about the same

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1216 9767488+ 83 Linux
/dev/sda2 1217 1338 979965 82 Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05316498

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9964 80035798+ 7 HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 60801 488384001 c W95 FAT32 (LBA)

Now, the first disk, the 200gb one has ubuntu installed on the second partition with the third as swap. Then XP is installed on the second one.

Ignore the third one.

Now, when I go to add XP, I modify it to look like this:

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Home
root (hd1,0)
savedefault
makeactive
chainloader +1

I think that this is correct, but im not sure. Now when I go to boot, I open up the boot menu and try to click on windows XP. It pulls up the loading setup... or something. I can't remember what it says. But it just hangs there. There is 0 hard drive activity and it is not loading. Why??!?!  ](*,)

---

### Post by kk0sse54 on 2008-05-16
My GRUB for windows is

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

hopes that helps maybe maybe not. Sounds like though you are pointing grub to the wrong place for xp.

---

### Post by bodhi.zazen on 2008-05-16
Windows is picky, wants to be on the master drive.

all you need do is add a "map"

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Home
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot
```

---

### Post by samknex on 2008-09-05
Well, here i am again with the same problem. Now it is on my parents computer. Im not even sure if a dual boot will work, but please prove me wrong. The sudo f-disk is as follows:


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a7a6c48

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extended
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081    c  W95 FAT32 (LBA)


Now. As you can probably tell, ubuntu is on the first hard drive. I have XP on the second. I have tried all possible entries, and nothing works. There either has to be a trick to it, or it will just flat out not work. Help Please!:confused:

---

### Post by caljohnsmith on 2008-09-05
Samknex, how about posting the full menu.lst from your parent's computer? Also, do you know which HDD boots on start up? And does Ubuntu boot fine, but just not Windows?

---

### Post by bodhi.zazen on 2008-09-05
you have to map your drives, see my previous post. If that does not work, as caljohnsmith suggests, post your *relevant* sections from /boot/grub/menu.lst (the windows stanza).

---

### Post by samknex on 2008-10-04
Ok, sorry. I havent been able to get to my parents computer until now. Here is my entire menu.lst. I know you only want the relevant parts, but many things are relevant. If it makes any more sense. The problem might be that XP is on the secondary, or slave drive. Ubuntu is on the primary drive, and i guess windows doesn't like that. This computer is practically ancient, its from 2001, with a P4 Processor and 256mb ram. now, if there isn't anything else, here is the menu.lst:

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
# kopt=root=UUID=54221cc0-b77b-484a-b3bd-c8190e439a58 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=54221cc0-b77b-484a-b3bd-c8190e439a58 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=54221cc0-b77b-484a-b3bd-c8190e439a58 ro single
initrd		/boot/initrd.img-2.6.24-19-generic


title 		Windows Xp
rootnoverify 	(hd0,0)
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Home
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1

Just in case you are wondering why there are like 3 XP versions, it is because i tried all of the ways you guys suggested, and yet it still doesn't work. Any help would be greatly arreciated  :)

---

### Post by caljohnsmith on 2008-10-04
Samknex, we're going to need more info from you if you want help booting Windows. :) First clarify: when you start up, do you get the Grub menu, and can you boot Ubuntu OK? If you can boot Ubuntu OK from Grub, that means your menu.lst entry for "Microsoft Windows XP Home" should work if your Windows is on the first partition of the 2nd boot drive. From your post 1 month ago though, sdb1 is a FAT32 partition; are you sure that is Windows? And can you boot Windows from that drive by setting that drive as the first to boot in BIOS on start up? What exactly happens when you choose the "Microsoft Windows XP Home" entry in Grub on start up? Any errors?

---

### Post by bumanie on 2008-10-04
> ## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=54221cc0-b77b-484a-b3bd-c8190e439a58 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=54221cc0-b77b-484a-b3bd-c8190e439a58 ro single
initrd /boot/initrd.img-2.6.24-19-generic


[COLOR="Red"]title Windows Xp
rootnoverify (hd0,0)
makeactive
chainloader +1[/COLOR]


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP [COLOR="Blue"]Media Center[/COLOR]
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

[COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
root (hd0,1)
savedefault
makeactive
chainloader +1[/COLOR]

[COLOR="Black"]I think you have got a bit confused with the suggestions that have been given. The entries in red, need to be deleted and the one in blue altered from "HOME" to "Media Center, although the last one is not that important as it is only a name[/COLOR]

---

### Post by samknex on 2008-10-05
Ok, here goes caljohnsmith. To answer your first Question, yes, the computer does start up, and it does give me the grub menu. I can select anything on the list, such as ubuntu or ubuntu safe mode. but none of the XP entries work. Second Question. Yeah you would think that it would work but it doesn't. Third Question. Man, i didn't even consider that the Fat32 formatting could have an impact. Yes, i am 100% sure that that is the windows partition. I can switch that hard drive to the primary instead of the secondary, and it works just fine. It is when it is in the secondary position that it will not work. And 4th Question. Sure, i will try that. give me a few minutes to get it worked out. And i will write down any errors that are reported. All of that will have to be done in a second post. This is being typed in the ubuntu installation, by the way. Be right Back.:)

---

