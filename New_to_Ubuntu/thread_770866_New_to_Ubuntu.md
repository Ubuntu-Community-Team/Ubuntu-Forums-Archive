---
title: "New to Ubuntu"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by burnfast81 on 2008-04-27
Hello everyone,

As the title suggests I am new to Ubuntu and Linux.  It's a whole different world from Windows that's for sure.  I currently have Windows Vista and Ubuntu Hardy Heron running on my PC.

My question is before upgrading to Hardy Heron I had the last version of Ubuntu and when I upgraded to Hardy Heron, GRUB for whatever reason still mentions the previous version and Hardy Heron along with Vista.  Is GRUB mentioning this because I didn't do something right and the previous version is still on there or is there a way to eliminate the choice of choosing the previous version of Ubuntu?  I did have GRUB programmed to load Vista 1st as other people use my computer, but I don't feel comfortable enough to mess with any of the (I guess its called) command lines in GRUB.

---

### Post by Joeb454 on 2008-04-27
You probably merged the 2 different grub files :)

---

### Post by Can+~ on 2008-04-27
It's not that difficult to edit them out:

```
gksudo gedit /boot/grub/menu.lst &
```

It looks like this:

So you can add "#" to comment out a section. Example, if I want to remove Windows from my list:


```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title		Microsoft Windows XP Professional
#root		(hd0,0)
#savedefault
#makeactive
#chainloader	+1
```

---

### Post by Aurora@FleetBuzz on 2008-04-27
If you've upgraded successfully, it's not difficult to edit out the references to Gutsy on your start up menu.  They are contained in your menu.lst file.  If you post a copy, we will be able to show you which entries to edit out.

Open a terminal and run this:
> cat /boot/grub/menu.lst
Copy and paste the results.

---

### Post by sailor2001 on 2008-04-27
when you bootup, your boot window will show all your loaders. Starting with Hardy heron, it will be '0' default.  Count down FROM there to your windows loader (probably 4?)  Now in gksudo gedit /boot/grub/menu.lst change the '0' default to the number you counted for windows. Save and exit

---

### Post by burnfast81 on 2008-04-27
> **Aurora@FleetBuzz said:**
> If you've upgraded successfully, it's not difficult to edit out the references to Gutsy on your start up menu.  They are contained in your menu.lst file.  If you post a copy, we will be able to show you which entries to edit out.

Open a terminal and run this:

Copy and paste the results.
Thanks for the suggestions guys.  Here's the code:

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
default		4

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
# kopt=root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,1)
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
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by Aurora@FleetBuzz on 2008-04-27
Bumping it up for you.

I think that you could safely edit these two entries out with the # sign as described above, but I'll defer to more experienced users.  Although these are labeled 8.04, I think they are actually referring to Gutsy.  
> title Ubuntu 8.04, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e734c181-c909-4e2c-bec7-25c266a79777 ro single
initrd /boot/initrd.img-2.6.22-14-generic


Can anyone verify and recommend that editing out should solve this?  I think you've successfully upgraded.  However, i can't explain why references to the old kernel would still show up?

---

### Post by abhiroopb on 2008-04-27
Just to confirm, yes commenting these out will be fine. This is just the older kernels, and you can potentially use them to run hardy (I did as my wireless card wasn't working with the newer kernel). In any case it doesn't matter either way, just comment it out. You should be using the newer kernel 2.6.24-16-generic

---

