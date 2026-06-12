---
title: "Ubuntu 8.04 upgrade problem."
date: 2008-05-06
forum: New to Ubuntu
---

### Post by brianstokes21 on 2008-05-06
Now that I upgraded to 8.04 from 7.10 Ubuntu will not start. It says loading  grub hit escape to enter menu then the screen goes blank and nothing happens.  
If I hit escape then I enter the menu I get a couple of options. When I choose to boot normally Ubuntu will actually load as if there were nothing wrong. Is there something wrong with the bootloader? Anyone have some suggestions?


Brian
Toshiba p4 3.06 Ghz 
1.5G of ram 
160G hard drive
ATI integrated graphics

---

### Post by quelx on 2008-05-06
Is the "Boot Ubuntu Normally" option not the default option when you get the selections screen?  If not you may need to tweak your /boot/grub/menu.lst file so the newer (and working) ubuntu kernel and installation boots.  If you can post that file it may help to diagnose.

---

### Post by brianstokes21 on 2008-05-06
I am going to eat some dinner. I will post the menu file in about an hour.
Pls check back.

---

### Post by brianstokes21 on 2008-05-06
okay so when I hit escape before the grub loads it takes me to selecion screen with two regular ubuntus 8.04 generic and two recovery. I select the recovery. Then I select boot normal. I can't attach the  menu file so I will just paste the text. Thx for the help.

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
# kopt=root=UUID=2ac637e4-ec9c-4720-8d3d-857056da5bc8 ro

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2ac637e4-ec9c-4720-8d3d-857056da5bc8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2ac637e4-ec9c-4720-8d3d-857056da5bc8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2ac637e4-ec9c-4720-8d3d-857056da5bc8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=2ac637e4-ec9c-4720-8d3d-857056da5bc8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by quelx on 2008-05-06
But all you see is a blank screen if you don't press any keys while it is booting, correct?  If you can edit the /boot/grub/menu.lst file and remove the **quiet** and **splash** from the non-recovery options so you can see what grub is saying (if anything) ```
ALT-F2 > **gksudo gedit /boot/grub/menu.lst**
``` and post what you see when you let it boot on it's own.  While your at it comment out (put a # in front of it) the **hiddenmenu** near the top so you can see what is selected by default (which appears to be the regular 2.6.26 kernel) for instance...

```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2ac637e4-ec9c-4720-8d3d-857056da5bc8 ro # quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
# quiet

```

let us know what you see without any interference from the keyboard.

---

### Post by brianstokes21 on 2008-05-06
Alright, I fixed it. I had to do this when i first installed Gusty. My PC does not like the quiet and splash thing inside the grub.

Open a Terminal and type

uname -r
and note the numbers here -- you will need them in a second
(mine is 2.6.24-16-generic)
Next, type:
sudo pico /boot/grub/menu.lst

enter you password

then scroll down until you see 

  title Ubuntu, kernel 2.6.24-16-generic
  root (hd0,0)
  kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=f795e1c7-6754-4d5a-accf-0e474a164b94 ro quiet splash
  initrd /boot/initrd.img-2.6.24-16-generic

just delete the quiet and splash then save and exit. 

Hope this can help somebody else.

---

