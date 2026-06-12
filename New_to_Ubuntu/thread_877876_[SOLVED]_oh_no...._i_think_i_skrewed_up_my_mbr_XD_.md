---
title: "[SOLVED] oh no.... i think i skrewed up my mbr XD help!"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by SchindlerShadow on 2008-08-02
ok hers wat happened, i have a 40gb hdd in hd(1,0) and a 160gb hdd with ubuntu installed on hd(2,0) i then installed windows on hd(1,1) and i reinstalled grub on hd(1,1) now i can boot to ubuntu but not windows XD what can i do? any help is appreciated. :confused::confused::confused:

---

### Post by SunnyRabbiera on 2008-08-02
well most likely XP is still there if you are lucky.
I see this issue often but to make sure can you see your windows drives in ubuntu?

---

### Post by powerpleb on 2008-08-02
> **SchindlerShadow said:**
>  i then installed windows on hd(1,1) and i reinstalled grub on hd(1,1)
You put grub on the Windows partition???

---

### Post by SunnyRabbiera on 2008-08-02
> **powerpleb said:**
> You put grub on the Windows partition???

seems like it, but I sure hope not o.0

---

### Post by bumanie on 2008-08-02
Post output of > sudo fdisk -lThat's a lower case L, not the digit one.

---

### Post by barkalot on 2008-08-02
You probably just have to add an option for Windows on your GRUB list. Open menu.lst as follows
```

gksudo gedit /boot/grub/menu.lst
```

Then, if you scroll down a bit you'll see a commented "examples". Copy the entry for Windows at the end of the Ubuntu automagic kernel's list and uncomment it. Then make sure the settings are appropriate. It seems you already know on which partition your Windows is so that won't be a problem. Make sure to uncomment.

I think this is how you do it, anyway :)

Edit: Since he can still boot into Ubuntu, then I assume that GRUB works properly and is on the correct partition.

---

### Post by SchindlerShadow on 2008-08-02
> **bumanie said:**
> Post output of That's a lower case L, not the digit one.

$ sudo fdisk -l 
[sudo] password for: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa70da70d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS
This disk has both DOS and BSD magic.
Give the 'b' command to go to BSD mode.

Disk /dev/sdb: 137.4 GB, 137437904896 bytes
255 heads, 63 sectors/track, 16709 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29a61531

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16064       16709     5188995   82  Linux swap / Solaris
/dev/sdb2               1       16063   129026016   83  Linux

Partition table entries are not in disk order
and yea i did install grub on the windows partition XD i thought that it would give windows as a boot option. XD

---

### Post by bumanie on 2008-08-02
Also post output of > cat /boot/grub/menu.lstWindows looka as though it is still there, but not sure what the reference to bsd is > This disk has both DOS and BSD magic.
Give the 'b' command to go to BSD mode.Have you ever had free bsd on the same hard drive?

---

### Post by SchindlerShadow on 2008-08-02
> **bumanie said:**
> Also post output of Windows looka as though it is still there, but not sure what the reference to bsd is Have you ever had free bsd on the same hard drive?

 cat /boot/grub/menu.lst 
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
# kopt=root=UUID=0076d821-6a62-432a-b230-8aead1d9a529 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0076d821-6a62-432a-b230-8aead1d9a529 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=0076d821-6a62-432a-b230-8aead1d9a529 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0076d821-6a62-432a-b230-8aead1d9a529 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0076d821-6a62-432a-b230-8aead1d9a529 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



and no, iv never ever have bsd. iv heard of it tho...... :confused:

---

### Post by sdowney717 on 2008-08-02
I dont see an entry for windows in that grub list
here is my windows entry
hd(0,0) is where my partition for xp is, just match that line where your windows partition is located.


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by SchindlerShadow on 2008-08-02
> **sdowney717 said:**
> I dont see an entry for windows in that grub list
here is my windows entry
hd(0,0) is where my partition for xp is, just match that line where your windows partition is located.


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

idk but i know that win is on this comp, i did it myself! my 1st hdd only has 1 partion, ntfs, my 2end 1 has 2 ext3 and linux-swap, cant  fix it so i can boot off win? cant i edit grub r something????? :confused::confused:

---

### Post by sdowney717 on 2008-08-02
yes, you can edit grub and add the xp entry to the list

enter this line to edit grub menu
open a terminal and put this in there

gksu gedit /boot/grub/menu.lst

---

### Post by SchindlerShadow on 2008-08-02
> **sdowney717 said:**
> yes, you can edit grub and add the xp entry to the list

how? can some1 explane it????

---

### Post by sdowney717 on 2008-08-02
[http://www.geocities.com/alavoor/resize_partition.html](http://www.geocities.com/alavoor/resize_partition.html)

read thru this and you will see a command called find

open a terminal
applications - acces - terminal

type in 
grub
this gives you a grub prompt

grub> 

type in find /boot/grub/stage1
I get (hd0,1)

grub> find /boot/grub/stage1
 (hd0,1)

type guit

edit your grub file
scott@scott-desktop:~$ gksu gedit /boot/grub/menu.lst 

and add in those lines I put in a previous post. You may have to adjust the root line depending on where your windows partition is located.

from the web page
Troubleshooting: Grub not finding file or disk or partition.

If the disk is not recognised inside the grub, then that partition is
marked as "hidden". Also when you do 'find /boot/grub/stage1' it does
not find the file. So you do this inside grub:
Note: hd0 is /dev/hda1  and partition 1 is 0 in grub commands.

grub> unhide (hd0,0)
grub> find /boot/grub/stage1  
(Now this will succeed and show some output)

---

### Post by SchindlerShadow on 2008-08-02
> **sdowney717 said:**
> [http://www.geocities.com/alavoor/resize_partition.html](http://www.geocities.com/alavoor/resize_partition.html)

read thru this and you will see a command called find

open a terminal
applications - acces - terminal

type in 
grub
this gives you a grub prompt

grub> 

type in find /boot/grub/stage1
I get (hd0,1)

grub> find /boot/grub/stage1
 (hd0,1)

type guit

edit your grub file
scott@scott-desktop:~$ gksu gedit /boot/grub/menu.lst 

and add in those lines I put in a previous post. You may have to adjust the root line depending on where your windows partition is located.

from the web page
Troubleshooting: Grub not finding file or disk or partition.

If the disk is not recognised inside the grub, then that partition is
marked as "hidden". Also when you do 'find /boot/grub/stage1' it does
not find the file. So you do this inside grub:
Note: hd0 is /dev/hda1  and partition 1 is 0 in grub commands.

grub> unhide (hd0,0)
grub> find /boot/grub/stage1  
(Now this will succeed and show some output)


ok thats a little confusing, can u give me a step by step plz? :)

---

### Post by SchindlerShadow on 2008-08-07
ok nvm i just installed opensuse on top of win! :lolflag: LINUX ROCKS! :guitar:

---

