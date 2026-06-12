---
title: "grub crashes when loading windows xp"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Chainek on 2008-08-15
I'll skip the "I'm a complete noob" bit and go straight to the problem..

I first installed xp home on an ntfs partition. Then install ubuntu, using the installer, I had it resize the partition automatically and install.

So now when I boot I get the grub boot loader. It loads into ubuntu just fine. When I select windows xp I see the xp loading screen for a split second followed by a blue screen with an error that really doesn't give much info.

Stop: 0x00000007b  bla bla bla bla bla bla bla bla bla  (just numbers)


Any suggestions? 

I appreciate it.

---

### Post by nicedude on 2008-08-15
Does Ubuntu boot correctly? Is there only one hard disk in this computer ? If the answers to those are both yes then there must be a problem with your menu.lst file which is where the XP loading command is located.

could you post back with the output of the following commands

sudo fdisk -l

and then lets copy your menu.lst file to the desktop so we can not risk messing it up

cp /boot/grub/menu.lst ~/Desktop/menulist.txt

now paste the contents of menulist.txt that is on your desktop here so all can look at it.

Armed with that I can tell you more

---

### Post by iaculallad on 2008-08-15
Boot using Ubuntu and post whatever displays when you issue the command below on your terminal:

```
cat /boot/grub/menu.lst
```

---

### Post by tech0007 on 2008-08-15
It's not a grub problem I believe.  Boot from you XP disk and run chkdsk /r.  You might also need to run fixboot after that but this command will ruin grub. So you need to reinstall grub using the liveCD.

---

### Post by Chainek on 2008-08-15
I have 2 hard drives in my computer.  C is partitioned with ubuntu/windows xp. E (I havn't looked at the drive letter yet.. asumming it's E) is just backup files.  Ubuntu works fine. Using right now to type this message. Xp was a fresh install. I booted it up once, worked fine. Restarted and installed ubuntu.


here is what comes up when I enter "cat /boot/grub/menu.lst" into terminal.



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
# kopt=root=UUID=ffcfda9e-7cfc-41eb-8d63-9fa4d2df7920 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ffcfda9e-7cfc-41eb-8d63-9fa4d2df7920 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ffcfda9e-7cfc-41eb-8d63-9fa4d2df7920 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Before I try fixboot.. I'll see if anybody else chimes in. 

Again I appreciate it.

---

