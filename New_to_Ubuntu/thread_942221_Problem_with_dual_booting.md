---
title: "Problem with dual booting"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by aunvoh on 2008-10-09
Ok, so i'm kind of new to this, i've been using ubuntu for about 2 days (like it a lot so far) but I need to be able to boot back into Windows XP, I installed XP and Ubuntu in seperate partitions. 

I edited my menu.lst to include:

title Windows XP
root (hd0,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Which got me Windows XP on my boot up grub menu, but after selecting Windows XP it just sits there and says "starting...." but does nothing else, i've tried replacing the 0's and 1's in the map lines. Still nothing, I really need to boot back into XP now, and would love any and all help anyone can offer me. 

If I didn't give enough info, or you have any questions, please just say what you need to know and i'll post it up.

Thanks again for your time.

---

### Post by bumanie on 2008-10-09
Welcome to ubuntu. Please post the output of > sudo fdisk -lu and > cat /boot/grub/menu.lst

---

### Post by aunvoh on 2008-10-09
Thanks and here you go.

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c90b741

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   149838254    74919096   83  Linux
/dev/sdb2       149838255   156296384     3229065    5  Extended
/dev/sdb5       149838318   156296384     3229033+  82  Linux swap / Solaris

> 
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
# kopt=root=UUID=50c2ffb4-1c3c-4772-9866-548ff915a4d0 ro

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
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50c2ffb4-1c3c-4772-9866-548ff915a4d0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=50c2ffb4-1c3c-4772-9866-548ff915a4d0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd0,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


---

### Post by bumanie on 2008-10-09
Try adding the bits I have highlighted in red to the /boot/grub/menu.lst

### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Red"]# This is a divider, added to separate the menu items below from the Debian
# ones.
title		      Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1[/COLOR]


title Windows XP
root (hd0,0)
[COLOR="Red"]savedefault[/COLOR]
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Hope it works.

---

### Post by aunvoh on 2008-10-09
Still doing exactly the same thing, any thoughts?

---

### Post by markgorelick on 2008-10-09
I have created a dual boot system, first installing Windows XP then Unbuntu 8.4.01.  I am having a problem with my Grub boot menu as it only stays up for selection for a fraction of a second, not long enough to make a selection.  I have a timeout value of 15 secs but I cannot figure out what else is happening.

Any suggestions??

---

### Post by kansasnoob on 2008-10-10
> **markgorelick said:**
> I have created a dual boot system, first installing Windows XP then Unbuntu 8.4.01.  I am having a problem with my Grub boot menu as it only stays up for selection for a fraction of a second, not long enough to make a selection.  I have a timeout value of 15 secs but I cannot figure out what else is happening.

Any suggestions??

For you, install startupmanager:

```
sudo apt-get install startupmanager
```

You'll then see it in System > Admin ......

No idea how to help the OP:(

---

