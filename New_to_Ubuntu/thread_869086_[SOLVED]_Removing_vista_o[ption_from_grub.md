---
title: "[SOLVED] Removing vista o[ption from grub"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-24
OK I've deleted my vista partition and now ubuntu uses the whole hardrive i want to remove the option for vista and and the ten second wait time before it boots Ubuntu

so far i have backed up my grub menu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

and opened up menu.lst

but what exactly do i remove? and what do i edit to speed up the boot time?
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
# kopt=root=UUID=4960185f-65a4-4451-b181-27d0866b6fad ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4960185f-65a4-4451-b181-27d0866b6fad ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4960185f-65a4-4451-b181-27d0866b6fad ro single
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
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Thanks in advance:KS

---

### Post by match002001 on 2008-07-24
I do not know how to make the boot faster for you but in order to rid of the Windows XP first make sure that you have that partition removed of XP otherwise i believe it will keep adding it. 

As far as removing it from GRUB you should be able to just remove the option at the bottom and then save the menu.lst file.

Hope this helps

-Match

---

### Post by o.besner on 2008-07-24
To change the "10 seconds", you need to edit the "timeout" line

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10   # change this to the number you want, I use 2

To remove the Vista option, remove this :

> # This is a divider, added to separate the menu items below from the Debian
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


---

### Post by Potatoj316 on 2008-07-24
To remove the XP option remove these lines (the bottom of the file)
```
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
```

If you change this 
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```
to this
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```you wont even see the GRUB menu, if you only have 1 OS this is usually nice

If you really dont ever think your going to want to enter the GRUB menu you can set timeout to 1, it makes it possible to enter the menu but you probably wont accidently do it and it dosent waste time waiting for you to push a key you wont ever push

---

### Post by philinux on 2008-07-24
Use gksudo gedit /boot/grub/menu.lst

Delete this bit at the bottom

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Look further up you'll see 
timeout 10 sec
Change it to something like 3

---

### Post by kamitsukai on 2008-07-24
Thanks everyone!

---

### Post by WRDN on 2008-07-24
You could remove the "quiet splash" words from the kernel lines. This will mean that, rather than the splash screen appearing, only text appears.
I personally prefer to only remove the word "quiet", as this allows for a splash screen/ loading bar, a list of services starting and whether or not they succeeded in starting.

---

### Post by silverglade00 on 2008-07-24
Unless you are getting rid of your Vista altogether, I would comment those lines out instead of deleting them. Just place a # character at the beginning of each line. However, you did back up your menu.lst, so you still have that backup to recover from.

---

### Post by philinux on 2008-07-24
> **kamitsukai said:**
> Thanks everyone!

Try installing and running startupmanager, it's in synaptic and the menu item appears in system>admin.

Really useful gui for changing boot stuff.

---

