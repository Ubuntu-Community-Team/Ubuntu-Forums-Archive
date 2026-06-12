---
title: "Busted Ubuntu Help!"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by goofeyfoot on 2008-05-30
I have been messing with Ubuntu for about a year.  I have learned very little but as time goes on I find I was using it more and liking it a little bit.

I got messing around with sound drivers and I must have busted something.

Anyway when I try to boot now a bunch of code comes up as Ubuntu is loading and then it says something to the effect of "Waiting for Root Files."  Something like that.  The screen is just text - there is no GUI.

I can't get past that point.

When I was messing with the sound I vaguely remember messing with a driver called "ctalas" or something to that effect.  I had some weird idea that it was messing up my sound so I told the program not to use ctalas any more.  I got a warning but who pays attention to those when you have no idea what they mean?

That was when the crystal went dark and I had no more Ubuntu.

But on a more positive note, I can sometimes boot up to a terminal.  And from there I can see that most of my stuff is still intact.  So it's there but I just can't boot up and fix anything.

So what do I do?  Do I have to wipe the drive and start over?  Or is there a way I can bust in and undo whatever I have wrecked?

Thanks for reading. 

Michael

---

### Post by spiderbatdad on 2008-05-30
[http://ubuntuforums.org/showthread.php?t=813178](http://ubuntuforums.org/showthread.php?t=813178)

---

### Post by InfinityCircuit on 2008-05-30
The link that was posted is answering a feature, not a bug, and does not relate to your problem.

The exact error message should be "Waiting for root filesystem."  This means that the root=XXX line in your /boot/grub/menu.lst is wrong.  If you can boot into a terminal, please post the contents of:

/boot/grub/menu.lst
/etc/fstab
ls -l /dev/disk/by-uuid

---

### Post by spiderbatdad on 2008-05-30
Well the things is...in 'messing around' with sound card...often folks remove alsa-base and ubuntu-desktop as a consequence. The fix might very well be to install ubuntu-desktop.

---

### Post by sports fan Matt on 2008-05-30
Im so glad I am not gonna try and bust my system lol..I feel your pain

---

### Post by goofeyfoot on 2008-05-30
Infinity Circuit:

Here is what I get from ls -l /dev/disk/by-uuid:

lrwyrwxrwy 1 root root May 30 19:38 [hex number] -> sdb5
lrwyrwxrwy 1 root root May 30 19:38 [hex number] -> sdb6
lrwyrwxrwy 1 root root May 30 19:38 [hex number] -> sda1
rwyrwxrwy 1 root root May 30 19:38 [hex number] -> sda5

Also, as far as the other two files are concerned how would I print out the contents of a file without a gui?  Gedit doesn't work in a terminal setting I don't believe.  I can't figure out how, in a terminal shell, to display the contents of menu.lst or fstab.  Is there a way to print to a screen or even a printer so that we can look at the contents of these files?

Thanks for your constructive suggestions.

Michael

---

### Post by Tatty on 2008-05-30
> **goofeyfoot said:**
> 
Also, as far as the other two files are concerned how would I print out the contents of a file without a gui? 

Boot to a live CD, then mount your hard drive :)

---

### Post by goofeyfoot on 2008-05-31
> **InfinityCircuit said:**
> The link that was posted is answering a feature, not a bug, and does not relate to your problem.

The exact error message should be "Waiting for root filesystem."  This means that the root=XXX line in your /boot/grub/menu.lst is wrong.  If you can boot into a terminal, please post the contents of:

/boot/grub/menu.lst
/etc/fstab
ls -l /dev/disk/by-uuid

Dear Infinity Circuit:

After some monkeying I was able to get the information that you wanted.

Here it is:

This is Menu.lst:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=01b7d579-53df-49db-b146-0e645fd21ba5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=01b7d579-53df-49db-b146-0e645fd21ba5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=01b7d579-53df-49db-b146-0e645fd21ba5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=01b7d579-53df-49db-b146-0e645fd21ba5 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=01b7d579-53df-49db-b146-0e645fd21ba5 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
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
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1



And here is the fstab:



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=01b7d579-53df-49db-b146-0e645fd21ba5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1db5a43d-cc50-4f16-87b6-439fef92f8b1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


And..last but not least here is the disk by uuid thing:

ubuntu@ubuntu:/media/disk$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-05-31 13:10 01b7d579-53df-49db-b146-0e645fd21ba5 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-31 13:10 01C7EE622BCE6220 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-05-31 13:10 01C7EE622D042300 -> ../../sdb6
lrwxrwxrwx 1 root root 10 2008-05-31 13:10 1db5a43d-cc50-4f16-87b6-439fef92f8b1 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-05-31 13:10 CAB2FDD0B2FDC0CD -> ../../hda1
lrwxrwxrwx 1 root root 10 2008-05-31 13:10 FCE8B922E8B8DBD8 -> ../../hda5
ubuntu@ubuntu:/media/disk$

---

