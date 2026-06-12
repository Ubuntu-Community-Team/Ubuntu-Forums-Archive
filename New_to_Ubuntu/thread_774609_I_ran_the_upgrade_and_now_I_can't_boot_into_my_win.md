---
title: "I ran the upgrade and now I can't boot into my windows partition"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by boriquajake on 2008-04-29
The upgrade seemed to go just fine and I am liking what I see so far. I am sure that whatever little issues there are will be fixed soon. My only concern so far is that since the upgrade windows doesn't show up as one of the boot options when I turn on the computer. Is there a simple way to fix this?

---

### Post by russ18uk on 2008-04-29
Can you post your /boot/menu.lst.

---

### Post by boriquajake on 2008-04-29
> **russ18uk said:**
> Can you post your /boot/menu.lst.

OK, this is odd, I open the terminal and after a few seconds it just hangs and goes all greyed out. I am pretty sure that is not supposed to happen. ;-)

Is there an alternative way of getting to terminal, or an alternate method of geting my /boot/menu.lst? Heck, I really am not ever sure how I would normally get that. I was going to open terminal and type that in to see what happened. I guess I should back up and say, yes, I will glady post my /boot/menu.lst, can you kindly tell me where to find it?

---

### Post by russ18uk on 2008-04-29
Open the run box and for kde you can use kwrite or gedit for gnome. Open a file like any other. Not sure if your broken terminal is linked but you may have a duff install. If you used a CD image to install do a check on the CD to make sure nothing was corrupt and the ISO if need be. Bittorrent is actually the best way of downloading since most clients will hash check the data.

---

### Post by shearn89 on 2008-04-29
hit alt-f2, then type "gedit /boot/grub/menu.lst".
Post it here.
Chances are the update nerfed your settings, and you just need to uncomment the windows partition at the end of the list.

---

### Post by russ18uk on 2008-04-29
> **shearn89 said:**
> hit alt-f2, then type "gedit /boot/grub/menu.lst".
Post it here.
Chances are the update nerfed your settings, and you just need to uncomment the windows partition at the end of the list.

Heh that's what I was trying to say :lolflag:

---

### Post by boriquajake on 2008-04-29
I can tell some things are sort of odd. I didn't mention that when I turn on the old lappy I am presented with two separate versions of 8.04 (both normal and "recover") plus the memtest. I just logged off and back on but this time I selected the second option and some of the twitchyness has gone away. For example the terminal window comes up with no problems and my browser seems less sluggish. Anyway, without further ado:

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# kopt=root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=24deff58-f29f-45cc-8074-4c559ce6da12 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by shearn89 on 2008-04-29
yep - assuming the windows partition is installed on the first partition on your disk, just uncomment that windows example.
```

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

```
If it isn't on sda1 (thats what it would be called in linux), then change "hd0,0" to "hd0,x" where x is the number of the partition.
For example, the first partition of my disk is my windows recovery one, then windows, then linux. So my hd line is "hd0,1".

---

### Post by boriquajake on 2008-04-30
> **shearn89 said:**
> yep - assuming the windows partition is installed on the first partition on your disk, just uncomment that windows example.
```

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

```
If it isn't on sda1 (thats what it would be called in linux), then change "hd0,0" to "hd0,x" where x is the number of the partition.
For example, the first partition of my disk is my windows recovery one, then windows, then linux. So my hd line is "hd0,1".

You guys are the best. Everything is working just fine.

---

### Post by boriquajake on 2008-04-30
I would like to mark this thread as "solved" but I don't see that option under "thread tools" anymore. What did I miss?

---

### Post by shearn89 on 2008-04-30
due to the forum upgrade, its broken/not implemented yet. Don't worry - it'll fade into the background soon enough, this subforum gets soooo many threads.

---

