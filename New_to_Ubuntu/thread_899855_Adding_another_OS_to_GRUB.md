---
title: "Adding another OS to GRUB"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by bgast1 on 2008-08-24
I have installed Slackware on my 2nd Hard drive, but did not install Lilo because I already had GRUB with my Ubuntu install. I would like to add this Slackware install to GRUB but don't know how. Can anyone help?

---

### Post by zamadatix on 2008-08-24
a simple forum search shows the way [http://ubuntuforums.org/showthread.php?t=219745]("http://ubuntuforums.org/showthread.php?t=219745")

---

### Post by bgast1 on 2008-08-24
Doesn't show me the way real clearly, sorry. I don't know how to mount Slackware in Ubuntu. It is installed on my 2nd hard drive which in sdb1.

---

### Post by zamadatix on 2008-08-24
oh i thought that was the other post on grub but it was different. 

sudo gedit /boot/grub/menu.lst 

go to the bottom of hte os list and type

title slackwares name
root (sdb1,0) *could be hd1 or hd2 also, type ":f -h" in the terminal to find out*
makeactive
chainloader +1

---

### Post by lswb on 2008-08-24
I don't think the chainloader statement will work without lilo or another bootloader installed on the partition being booted. Assuming that slack has the usual kernel and initramfs files, you can use the lines that boot ubuntu in menu.lst as a model to add another choice to boot slackware. Check out this web page, this guy has got it all covered: 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

and check out the home page from that site also.

---

### Post by bgast1 on 2008-08-24
This is what I did and it doesn't work. 

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
# kopt=root=UUID=5abd691c-95b9-48ed-8d42-3b5bf7fba999 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5abd691c-95b9-48ed-8d42-3b5bf7fba999 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5abd691c-95b9-48ed-8d42-3b5bf7fba999 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title          Slackware Linux
root           (sdb1,0)
makeactive	
chainloader +1
```

---

### Post by zamadatix on 2008-08-24
did you try lswb's link. as stated chainloader wont work apparerntly.

---

### Post by bgast1 on 2008-08-24
> **lswb said:**
> I don't think the chainloader statement will work without lilo or another bootloader installed on the partition being booted. Assuming that slack has the usual kernel and initramfs files, you can use the lines that boot ubuntu in menu.lst as a model to add another choice to boot slackware. Check out this web page, this guy has got it all covered: 

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

and check out the home page from that site also.

So I'm guessing that it would have made sense to install LILO. Would LILO have overwritten GRUB?

---

### Post by zamadatix on 2008-08-24
probably. jsut a quick question can you have both grub and lilo soemhow? (have lilo open grub ar vicea versa?) or would that not work.

---

### Post by SuperSonic4 on 2008-08-24
I suspect Lilo would not overwrite grub unless you specifically put it on the grub drive. The simplest solution seems to be installing lilo on one HDD for Slackware and grub on the other for ubuntu and changing at the bios

---

### Post by lswb on 2008-08-24
You can install lilo on the drive with slackware and then the chainloader statement should work. Or you can identify the slackware kernel and initramfs in a grub menu.list stanza and use grub to boot slack from the same menu that boots ubuntu. Personally I would forget about lilo just because I am more familiar with grub. There are really several workable options. Check out the web site linked to earlier in this thread for a good explanation.

---

