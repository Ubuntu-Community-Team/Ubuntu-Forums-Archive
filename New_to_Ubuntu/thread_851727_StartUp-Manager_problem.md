---
title: "StartUp-Manager problem"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by s1337m on 2008-07-06
I installed StartUp-Manager and edited my settings, but now everytime I load/shutdown ubuntu the splash screens are messed up; im not sure how to describe this but the colors are way off.  im using hardy 8.04, kernel 2.6.24-19-generic.

---

### Post by Bubba64 on 2008-07-07
Did you tick the appearances settings you can turn them off.

---

### Post by s1337m on 2008-07-09
> **Bubba64 said:**
> Did you tick the appearances settings you can turn them off.

i edited the number of color bits to use, so the startup and restart splashes work but not the shutdown... but 2/3's good enough. :popcorn:

---

### Post by Bubba64 on 2008-07-09
I can't remember how to do it but you can easily change the splash screen colors if that is what your trying to do, I looked around and couldn't find the control.

---

### Post by dentaku65 on 2008-07-09
Changing the Color depth to 16 should be fix this

---

### Post by s1337m on 2008-07-09
> **dentaku65 said:**
> Changing the Color depth to 16 should be fix this

thanks, all the screens are okay now... but, after choosing ubuntu at grub, i get the message:

Undefined video mode: 2f6
Choose a new one, hit space to continue or wait 30 sec.

If i hit space or wait, the screens okay... is there a way to disable this message?

i also tried choosing a new one, but the choice doesnt stick for the next boot

---

### Post by dentaku65 on 2008-07-10
Can you post the output of:

```
sudo cat /boot/grub/menu.lst
```

---

### Post by iaculallad on 2008-07-10
*When you first execute SUM, it saves a copy of your current menu.lst file as /boot/grub/menu.lst.backup*

To revert changes back to original settings because of irregularities:

```
sudo mv /boot/grub/menu.lst.backup /boot/grub/menu.lst
```

---

### Post by s1337m on 2008-07-12
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
color cyan/blue white/blue

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
# kopt=root=UUID=a082f49a-f14b-4d6d-9253-a61a8b6e4e58 ro

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
# defoptions=splash vga=786

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
# howmany=2

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a082f49a-f14b-4d6d-9253-a61a8b6e4e58 ro splash vga=786
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=a082f49a-f14b-4d6d-9253-a61a8b6e4e58 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a082f49a-f14b-4d6d-9253-a61a8b6e4e58 ro splash vga=786
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a082f49a-f14b-4d6d-9253-a61a8b6e4e58 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[sean@sean-laptop:~] 


```

i like the feature of SUM that controls what kernel shows up on grub, so i would like to keep it.  this splash screen isnt that big of a deal in comparison

---

