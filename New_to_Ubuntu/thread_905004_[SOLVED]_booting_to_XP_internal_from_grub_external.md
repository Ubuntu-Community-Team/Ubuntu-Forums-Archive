---
title: "[SOLVED] booting to XP internal from grub external?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by jimmgunnz on 2008-08-29
okay.  so, very basics....

laptop...
internal hard drive = XP
with
external hard drive = Ubuntu

grub works great for Ubuntu (installed to external); booting is smooth, all is pretty good except for just a couple minor inconveniences, which is where you come in =]

when in grub, it lists all of my available OSs, including XP.  from grub, if i try to boot to XP, it fails.  i'm guessing because it's looking to the external hard drive for XP, but XP is on the internal drive.  so it seems it may be a mapping problem of sorts, but i have no idea how to figure it out.

i know people usually want some output of sorts, so if anyone wants to help me out, you can ask and i'll gladly continue with posting that stuff =]

much thanks in advance....

---

### Post by overdrank on 2008-08-29
Moved to ABT :)

---

### Post by gmxgeek on 2008-08-30
Can you get a list of devices? Which hdd is xp on, and what does /boot/grub/menu.lst say it is trying to boot to?

---

### Post by caljohnsmith on 2008-08-30
As gmxgeek alluded to, please post the output of the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by jimmgunnz on 2008-08-30
sorry, didn't realize this was ABT.  i actually haven't seen this situation in any threads (and i have searched!), it seems everyone is doing dual boots in the same internal or dual on the same external.  anyway... thanks for the interest!  here's the output requested.... let me know if i can provide other info!

fdisk -lu output:
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *    14346045   213552044    99603000    7  HPFS/NTFS
/dev/hda2              63    14346044     7172991    b  W95 FAT32
/dev/hda3       213552045   234436544    10442250    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5ee825ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     7807589     3903763+  83  Linux
/dev/sda2         7807590    15615179     3903795   82  Linux swap / Solaris
/dev/sda3        15615180   171863369    78124095   83  Linux
/dev/sda4   *   171863370   490223474   159180052+   6  FAT16


cat /boot/grub/menu.lst output:
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
# kopt=root=UUID=d5805dd5-279d-4ed7-88ba-77b3f62bf0dc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5805dd5-279d-4ed7-88ba-77b3f62bf0dc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d5805dd5-279d-4ed7-88ba-77b3f62bf0dc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows XP Media Center Edition
root		(hd1,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
chainloader	+1

---

### Post by caljohnsmith on 2008-08-31
> **jimmgunnz said:**
> 
title		Windows NT/2000/XP
root		(hd1,1)
savedefault
chainloader	+1
It looks like your above menu.lst entry for Windows is incorrect, because from your fdisk output, hda1 is your bootable Windows partition. Also, when booting Windows from a HDD that is not first in the boot order, you have to use Grub's "mapping" technique to fool Windows into thinking it is on the boot HDD. Therefore, I think you need to change the entry above to:
```
title		Windows XP
root		[COLOR="Blue"](hd1,0)[/COLOR]
[COLOR="Blue"]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
makeactive
chainloader	+1
```
And to make the above changes in menu.lst, just do:
```
gksudo gedit /boot/grub/menu.lst
```
Let me know how it goes or if you need more details/info. :)

---

### Post by jimmgunnz on 2008-08-31
who's a ninja??  you're a ninja! 

worked perfectly.  i had to do it thru regular sudo though, because gksudo for some reason doesn't work for me...

result is the same... total bootability of all of my OSs, no need to jump up and turn off my external just to go back to windows.

top notch.  much appreciated.  one more nemesis... wireless!!!  but that's another thread to be started shortly =]

---

### Post by jimmgunnz on 2008-08-31
oh, yeah, not sure how to mark something solved, so.... here it is in reply form =]

---

### Post by caljohnsmith on 2008-08-31
Glad at least that problem is fixed, jimmgunnz. :) By the way, if you go to the top of this thread and click the "thread tools" menu, you can mark it as "solved".

---

### Post by jimmgunnz on 2008-08-31
noted and marked.

thanks again for the help and quick responses!!

---

