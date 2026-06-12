---
title: "[SOLVED] How do I add VISTA to GRUB boot loader?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by maduranga on 2008-11-28
I have vista installed on my pc. But after ubuntu is installed, I cant boot into vista. Vista is not listed in boot loader.

Here is my /boot/grub/menu.lst

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
# kopt=root=UUID=ecd04ea8-8a78-46a9-a63d-e338c1b02eed ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ecd04ea8-8a78-46a9-a63d-e338c1b02eed

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ecd04ea8-8a78-46a9-a63d-e338c1b02eed
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecd04ea8-8a78-46a9-a63d-e338c1b02eed ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ecd04ea8-8a78-46a9-a63d-e338c1b02eed
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ecd04ea8-8a78-46a9-a63d-e338c1b02eed ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		ecd04ea8-8a78-46a9-a63d-e338c1b02eed
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


This is my partition information  

[IMG]http://i293.photobucket.com/albums/mm69/da_coolest_photos/gparted.jpg[/IMG]

(vista is installed in a separate hard disk.)

[IMG]http://i293.photobucket.com/albums/mm69/da_coolest_photos/gparted_vista.jpg[/IMG]


please tell me how to add vista to the grub boot loader! 

Thanks in advance!

---

### Post by nhasian on 2008-11-28
the super grub disk can fix that for you

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by adult swim on 2008-11-28
if you are lucky, you can add ```
title		Vista
root		(hd1,0)
chainloader	+1
``` to the end of your menu.lst and it will work.

---

### Post by maduranga on 2008-11-28
> **adult swim said:**
> if you are lucky, you can add ```
title		Vista
root		(hd1,0)
chainloader	+1
``` to the end of your menu.lst and it will work.

thanks! I'll try that!

EDIT: tried and failed! seems to be I'm not lucky! I get the following error when I select "vista" from boot menu

"BOOTMGR is missing"

---

### Post by adult swim on 2008-11-28
what is that /dev/sda1 on your first drive?

---

### Post by falcon61102 on 2008-11-28
The BOOTMGR missing error may be generated when Vista can no longer find it's boot loader because it has been overwritten.  

It appears that Vista is installed on your second HD, has it always been that way?

---

### Post by bcd87 on 2008-11-28
Edit: never mind, wrote some bs here :P

---

### Post by maduranga on 2008-11-28
Thanks all for helping. I found the solution. Previously I had ubuntu wubi installed and I deleted the "Ubuntu" folder cos the uninstaller wasn't working! deletion has broke MBR. I had to re-install it using vista recovery cd. then supergrub!

---

