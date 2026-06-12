---
title: "Grub, Extra Ubuntus"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by White_Sabre on 2008-05-19
Hey,
I have this thing when I load up into grub I have around 4 different versions of Linux (Ubuntu). Only the top version (Biggest number :) ) works while the rest go into some command line thing. 

So I figure you have to edit the file (can't remember name) but 
a) I don't know what I'm changing
and
b) I cant save the file

Also, while I'm at it how do I change Vista to the top so it auto-boots into it instead of Linux.

Anyway, hope you out there can help me with this.
Thanks :KS

Solved :) [cant edit title so sorry]

---

### Post by overdrank on 2008-05-19
> **White_Sabre said:**
> Hey,
I have this thing when I load up into grub I have around 4 different versions of Linux (Ubuntu). Only the top version (Biggest number :) ) works while the rest go into some command line thing. 

So I figure you have to edit the file (can't remember name) but 
a) I don't know what I'm changing
and
b) I cant save the file

Also, while I'm at it how do I change Vista to the top so it auto-boots into it instead of Linux.

Anyway, hope you out there can help me with this.
Thanks :KS
HI and you will need to edit your grub menu list 
```
gksudo gedit /boot/grub/menu.lst
```
And to change the default OS this link is great for the grub
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by White_Sabre on 2008-05-19
Thanks, the grub option things looks complicated. Could I like upload it, because it's quite confusing the link.

---

### Post by overdrank on 2008-05-19
> **White_Sabre said:**
> Thanks, the grub option things looks complicated. Could I like upload it, because it's quite confusing the link.

Hi and post your menu list and we can help

---

### Post by White_Sabre on 2008-05-19
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
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

```

The second Windows Vista is some backup thing. So I still need that just in case ^^

---

### Post by shadow-of-sin on 2008-05-19
Remove the following from your menu.lst and save the file:
```

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.20-15-generic


```

Those are simply references to old kernels.

---

### Post by SIXAXIS on 2008-05-19
Here:
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		3

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
# kopt=root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro

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

title		Ubuntu 7.10
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, kernel 2.6.20-16-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-16-generic
#quiet

#title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
#initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu 7.10, kernel 2.6.20-15-generic
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet

#title		Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu 7.10, memtest86+
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
makeactive
chainloader	+1
```

I commented out all the lower kernel numbers. I made the first Vista installation the default, but why do you have 2 Vista installations?

**Or, if you want to put this in. It's a bit shorter and cleaner. I has the 2 Vistas first, then the Ubuntu, then the Ubuntu recovery, and then the Memory Test.**

```
default		0

timeout		10

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


title		Windows Vista/Longhorn (loader)
root		(hd0,1)
makeactive
chainloader	+1


title		Ubuntu 7.10
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6ef20938-ca54-417b-8703-cc18a9f0dd28 ro single
initrd		/boot/initrd.img-2.6.22-14-generic


title		Ubuntu 7.10 Memory Test
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

---

### Post by overdrank on 2008-05-19
You may choose not to remove but to place a # comment so they will not be seen but can be used in the future.
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by Shazaam on 2008-05-19
You could comment (#) out the unneeded listings if you want. Keep the latest (newest) one including the Recovery kernel. I usually keep the latest one and one back in case I trash the newer one. :)
A cool app (in the repo's) is startupmanager. As always be careful with what you tweak using it.

---

### Post by White_Sabre on 2008-05-19
> 
I commented out all the lower kernel numbers. I made the first Vista installation the default, but why do you have 2 Vista installations?

Its a Back-Up thing that came with my computer ^^.

Also thanks everyone! :)

Going to Try load it up now bbs

---

