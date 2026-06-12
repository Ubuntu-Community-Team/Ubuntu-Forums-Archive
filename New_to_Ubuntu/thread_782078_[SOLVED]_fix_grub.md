---
title: "[SOLVED] fix grub"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-05-04
ok....   i bought this laptop about 6 or 7 months ago (it came with vista)

i shrunk my vista partition and installed ubuntu gutsy to the unallocated space

then windows vista died.. just completely stopped working, couldnt even boot to recovery mode

so i continued to use ubuntu gutsy untill hardy was released, then i installed hardy beside gutsy on the old windows vista partition

after getiing hardy all setup i decided to delete gutsy and try out some other distros while i had the available free space, so i instaled debian on the old gutsy partition 
(this wrote over my existing grub and replaced it with an ugly blue one)

after deciding id rather just stick with ubuntu i deleted debian and used this link, the first post, to restore my old (black) grub 
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

after a couple of days i decided to reinstall vista on the old debian/gutsy partition, in doing this vista wrote over grub with the default vista bootloader

so after i installed vista i used the same link as above to restore my grub again..

now the problem is grub still thinks gutsy is on dev/sda3 (where vista is now)

how can i configure grub to recognize my vista partition?


EDIT: heres my menu.lst
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
# kopt=root=UUID=3261a2f6-7bbf-4cdf-b21a-127015e0b240 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3261a2f6-7bbf-4cdf-b21a-127015e0b240 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3261a2f6-7bbf-4cdf-b21a-127015e0b240 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=36c2bf6e-77d5-493c-ae87-6b77c26749b9 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=36c2bf6e-77d5-493c-ae87-6b77c26749b9 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 7.10, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

---

### Post by jimv on 2008-05-04
See the line in your menu.list that says hd0,0?  You need to change that to point to your Ubuntu partition.  hd0,0 is hard drive 1, partition 1.

---

### Post by forrestcupp on 2008-05-04
[Here are instructions](http://ubuntuforums.org/showthread.php?t=224351) on how to restore GRUB.

---

### Post by kansasnoob on 2008-05-04
It looks to me like JimV has it right, but this is a great GRUB primer:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

It's bailed me out of quite a few troubling situations.

---

### Post by tjwoosta on 2008-05-04
> 
See the line in your menu.list that says hd0,0? You need to change that to point to your Ubuntu partition. hd0,0 is hard drive 1, partition 1.


? my ubuntu partition is hd0,0

hardy boots fine, my problem is getting gruub to recognize that gutsy is no longer on hd0,2  

right now theese are my partitions   
hd0,0 = Hardy  hd0,1 = Linux Swap  hd0,2 =Vista

grub still thinks i have gutsy on hd0,2 
(i need it to see that hd0,2 is actually windows vista)


> 
Here are instructions on how to restore GRUB.


thats actually the same link that i used and mentioned in my first post

---

### Post by jimv on 2008-05-04
> **tjwoosta said:**
> ? my ubuntu partition is hd0,0

hardy boots fine, my problem is getting gruub to recognize that gutsy is no longer on hd0,2  

right now theese are my partitions   
hd0,0 = Hardy  hd0,1 = Linux Swap  hd0,2 =Vista

grub still thinks i have gutsy on hd0,2 
(i need it to see that hd0,2 is actually windows vista)




thats actually the same link that i used and mentioned in my first post

OOPS.  My bad.  Just replace the Gusty entry with this:

> title		Windows Vista
root		(hd0,2)
makeactive
chainloader	+1


---

### Post by tjwoosta on 2008-05-04
thanks, that worked great

---

