---
title: "[SOLVED] Can't boot into Windows anymore! :("
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Sarah L on 2008-06-21
I've recently set up a dual-boot system with Windows XP installed first and Ubuntu Hardy installed over it. Both operating systems loaded fine before, but now selecting Windows gives me the following GRUB error:
```
Error 28: Selected item cannot fit into memory
```

This happened after I tried to use the grub-reboot command. Booting into Ubuntu or memtest86+ gives me no problems. I've tried running update-grub but it doesn't fix the problem.

Does anyone know what's wrong?

Thanks,
Sarah

---

### Post by cariboo on 2008-06-21
This seems to be a hard error to track down. The only advice I can give you is to re-install grub.

Jim

---

### Post by meierfra. on 2008-06-21
Post the output of 

```
cat /boot/grub/menu.lst
```

```
cat /boot/grub/default
```


```
sudo fdisk -l
```
(both l are lower case L)

---

### Post by fatality_uk on 2008-06-21
This link gives details:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319837](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319837)
The best bet is to re-install GRUB from what I have read.

Here's google's take on it
[http://www.google.co.uk/search?q=grub+Error+28&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a](http://www.google.co.uk/search?q=grub+Error+28&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-GB:unofficial&client=firefox-a)

---

### Post by Sarah L on 2008-06-21
Here's menu.lst:
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
# kopt=root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=7121b012-b675-4777-ae37-fd0f4c6e51e9 ro single
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
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

Here's the default file:
```
8
```
For some reason, opening it up in a GUI text editor causes complaints about "this is a binary file".

Here's my partition table:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24418768+   7  HPFS/NTFS
/dev/sda3            3041        8754    45897705   83  Linux
/dev/sda4            8755        9158     3245130    5  Extended
/dev/sda5            8755        9158     3245098+  82  Linux swap / Solaris

```

---

### Post by meierfra. on 2008-06-21
Well, I don't have any better suggesting then the others: reinstall grub

In a terminal

```
sudo grub
```

and  at the "grub"" prompt


```
root (hd0,2)
setup (hd0)
quit
```

If that did not solve the problem

```
gksudo gedit /boot/grub/menu.lst
```

change 

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


to

title		Microsoft Windows XP Professional
root		(hd0,0)
#savedefault
makeactive
chainloader	+1

---

### Post by meierfra. on 2008-06-21
One more thing to try:


```
sudo rm /boot/grub/default
sudo grub-set-default 0
```

---

### Post by Sarah L on 2008-06-21
I tried both
```
root (hd0,2)
setup (hd0)
quit
```

and

```
sudo rm /boot/grub/default
sudo grub-set-default 0
```

and it worked! Thank you! :)

---

