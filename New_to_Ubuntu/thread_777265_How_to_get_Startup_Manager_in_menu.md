---
title: "How to get Startup Manager in menu?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by chchandler on 2008-05-01
OK, 7.10 is running well.  I did a dual install, and in term I can read the grub manual and run grub... but I'm hesitant to run it via term.

I read the graphical grub interface should be in System/Administration/Startup Manager but I have no such entry.

Any step by step help for getting it there so I can set up for a dual boot?

Thanks!

---

### Post by gandaran on 2008-05-01
you have to install it
open synaptic, find startup manager, check for install and click apply.

startup manager doesn't set up dual boot!

---

### Post by chchandler on 2008-05-01
Well, I could easily be mistaken.  Is there a graphical interface to grub?  I thought it was Startup Manager.  I don't see it in Synaptic.  

I need to be able to boot into either Ubuntu or WinXP.  What's my easiest/simplest way to set this up?

---

### Post by skymera on 2008-05-01
As said above, it's in the repositories.

Dual boot is done via GRUB.
You can edit grub with this:

```
 
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup 
gksudo gedit /boot/grub/menu.lst 
```

Be careful editing it.
The first code is a copy code to make a backup.

---

### Post by gandaran on 2008-05-01
post the output of,   gedit /boot/grub/menu.lst  and   gedit /etc/fstab


have you enabled the repositories? startup manager should be there!

---

### Post by chchandler on 2008-05-01
Found startup manager and installed it, but there was no WXP partition.  Hmmm, it seems I have lost my WXP?  I browsed the file system and see no WXP stuff.  

There wasn't anywhere in the install where it asked me if I wanted to keep or trash my WXP... altho there was a part about importing the WXP user (prior user).  Maybe I should have imported him?

On boot now I get only linux, safe mode and mem check.  

Do you still need the outputs posted?

---

### Post by chchandler on 2008-05-01
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
timeout		8

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
# kopt=root=UUID=668a5ee4-ab29-4a51-b58b-fe752bea7578 ro

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
# defoptions=quiet splash vga=794

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=668a5ee4-ab29-4a51-b58b-fe752bea7578 ro quiet splash vga=794
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=668a5ee4-ab29-4a51-b58b-fe752bea7578 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by chchandler on 2008-05-01
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=668a5ee4-ab29-4a51-b58b-fe752bea7578 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=77efa448-0afc-4c57-8c0c-19ff85206485 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by gandaran on 2008-05-01
looks like you did wipe xp.
install gparted, it'll show you all the partitions on disk.

---

