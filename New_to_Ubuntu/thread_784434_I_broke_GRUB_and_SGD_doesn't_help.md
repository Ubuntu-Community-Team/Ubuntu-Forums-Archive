---
title: "I broke GRUB and SGD doesn't help"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by mnr82 on 2008-05-06
Hello

After installing ubuntu 8.04 (desktop) on a third HDD (win XP already installed on 1st) I did not get GRUB boot selection after reboot - instead it went straight to XP.
So I tried again, this time assigning GRUB to HD0 (i think) because I thought maybe grub had gone to HD3 which would not be seen on boot.

Now when I start the pc the word " GRUB " will appear, then nothing. If I try to repair grub, or remove and replace with the windows MBR thingy, both using super grub disk and winXP recovery with the XP disc, i will still end up with that " GRUB "  word after which nothing happens.

Any suggestions? As long as I can manage to get XP to start again, all should be clear. tyvm

---

### Post by tjwoosta on 2008-05-06
boot the live cd 

then open a terminal and do this

```

gedit /boot/grub/menu.lst

```

post whatever comes up

---

### Post by mnr82 on 2008-05-06
below are the contents of the /boot/grub/menu.lst located on the partition I installed 8.04 (the third hard drive, if i simply do ' gedit /boot/grub/menu.lst ' from live cd nothing happens since there is no folder grub and thus no menu.lst there). 
I considered a possible solution could be that the pc should actually boot from this drive but the problem is that I seem to only be able to select the two other drives in BIOS. 
If I'm talking nonsense here, apologies ;) here's that menu.lst:

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
# kopt=root=UUID=2accbeac-6f4b-46ca-8420-0a54b18e32c5 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2accbeac-6f4b-46ca-8420-0a54b18e32c5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2accbeac-6f4b-46ca-8420-0a54b18e32c5 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



---

### Post by tjwoosta on 2008-05-06
> from live cd nothing happens since there is no folder grub

o yea sry.. i was thinking like you were on the installed ubuntu rather than the live cd

you would have had to go to places then to your ubuntu harddrive
then to boot then grub then menu.lst

but anyway im not really expert at this or anything but where it says 
```

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,2)

```

that is implying that ubuntu is on hd0,2 
(which would be harddisk 1 partition 2)

if your ubuntu is on the first partition of a third harddisk i think it should be like this
(hd2,0)

as far as i know it goes like this  

harddrive 1 partition 1 = hd0,0
harddrive 1 partition 2 = hd0,1

and so on
then 

harddrive 2 partition 1 =hd1,0

you get the idea

(again im not 100% that this is what you should do in this case) but its worth a try


also try adding makeactive to the part that says 
```

title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```
so it looks like this
```

title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

```

of course thats if xp is actually on (hd1,0) 

just out of curiosity 
(you say you have xp and ubuntu each on a hdd, so whats on the other hdd)

here is a link to a post that may help
[http://ubuntuforums.org/showthread.php?t=774379&highlight=install+seperate+hdd]("http://ubuntuforums.org/showthread.php?t=774379&highlight=install+seperate+hdd")

---

