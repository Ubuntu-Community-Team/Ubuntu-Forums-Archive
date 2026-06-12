---
title: "Grub: weird characters"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Stefanie on 2008-06-25
i just installed ubuntu on my parent's computer (i'm already using ubuntu on my laptop) and there's a weird problem... when the grub bootloader shows up it says "ubuntu 8.04" , but the line for windows XP is completely unreadable (weird characters). Windows XP boots fine, though. i've tried changing the title of windows in /boot/grub/menu.lst , but that didn't help.

---

### Post by drs305 on 2008-06-25
Stefanie,

I think it was you that had problems earlier concerning an abnormally long boot process. I think you solved it by changing the boot resolution through StartUp-Manager. 

Is this the same machine? Perhaps you could try a different resolution (back to 640x480) to see if that resolves the problem. Or is it just some of the characters, with the rest being ok?

---

### Post by Stefanie on 2008-06-25
i'm sorry, but i never posted about abnormal boot processes. this is a very fresh install of ubuntu :-) 

the problem is only with the windows-line and the line above, nothing else.

---

### Post by drs305 on 2008-06-25
Did you manually cut & paste any entries into the menu.lst file? You might try copying the offending lines and pasting them into a plain text editor; then copy them back just to ensure there is no formatting issue. You also might go into StartUp-Manager  (System, Admin, StartUp-Manager if it's installed) and in the Appearance tab make things as simple as possible to eliminate other problem areas.

---

### Post by Inxsible on 2008-06-25
could you also post the contents of the menu.lst file here?

Btw, what is your keyboard layout set to on your parent's machine?

---

### Post by Stefanie on 2008-06-25
the menu.lst file looked normal, as far as i could see. i can't post its contents right now, ubuntu doesn't boot anymore now i installed the proprietary ATI driver :-( i will boot the livecd as soon as i can, my brother just booted into windows to do something "urgent" :roll:

---

### Post by drs305 on 2008-06-25
I guess another question that should have been asked earlier: is this happening only in the grub menu? Once you get to the desktop have you seen the effects anywhere else?

---

### Post by Stefanie on 2008-06-25
it also happens when i boot in recovery mode. i tried this because of the problem with the ATI-driver: ubuntu doesn't boot anymore so i tried recovery mode, everything went fine in the beginning (i could see the different processes being started etc) but then there was a kind of menu with three options, all of them completely unreadable :-?

---

### Post by Stefanie on 2008-06-25
i reinstalled, still the same problem with grub. menu.lst: 
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
# kopt=root=UUID=c67e17d4-fc42-495b-bcef-367a5b32ebcf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c67e17d4-fc42-495b-bcef-367a5b32ebcf ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c67e17d4-fc42-495b-bcef-367a5b32ebcf ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
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

```

---

