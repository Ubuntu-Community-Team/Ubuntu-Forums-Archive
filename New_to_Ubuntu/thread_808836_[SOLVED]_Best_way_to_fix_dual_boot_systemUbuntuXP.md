---
title: "[SOLVED] Best way to fix dual boot system/Ubuntu/XP"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by discmaster on 2008-05-26
I recently installed 8.04 (Heron) on my Sata drive. I have Win XP on another drive (Pata) in this pc. Before the upgrade to 8.04, I was using 7.10 with the dual boot & I got the selection screen at bootup.

Now after this install, I get the selection screen & XP is listed there, but when I select it, I get "NTLDR is missing". If I go into the BIOS & boot to that drive first, XP will load just fine, so I know it is okay.

I need to know how to get Linux to allow me to dual boot as before. How do I configure this to work? I am sure it is an easy fix, but I am a linux noob, so I need your help!

Thanks in advance!

:)

---

### Post by logos34 on 2008-05-26
post your /boot/grub/menu.lst

---

### Post by iaculallad on 2008-05-26
> **discmaster said:**
> I recently installed 8.04 (Heron) on my Sata drive. I have Win XP on another drive (Pata) in this pc. Before the upgrade to 8.04, I was using 7.10 with the dual boot & I got the selection screen at bootup.

Now after this install, I get the selection screen & XP is listed there, but when I select it, I get "NTLDR is missing". If I go into the BIOS & boot to that drive first, XP will load just fine, so I know it is okay.

I need to know how to get Linux to allow me to dual boot as before. How do I configure this to work? I am sure it is an easy fix, but I am a linux noob, so I need your help!

Thanks in advance!

:)

Select Ubuntu and boot from it. Post the output of **fdisk -l** and **cat /boot/grub/menu.lst**. Issue both command on your terminal.

---

### Post by cdtech on 2008-05-26
Boot with the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will put you into a "grub>" shell (i.e. the grub prompt). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd1,5) then you would enter root (hd1,5)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Then reboot without the CD.

---

### Post by oedha on 2008-05-26
or supergrubdisk can also help :)

---

### Post by Living2007 on 2008-05-26
> **discmaster said:**
> I recently installed 8.04 (Heron) on my Sata drive. I have Win XP on another drive (Pata) in this pc. Before the upgrade to 8.04, I was using 7.10 with the dual boot & I got the selection screen at bootup.

Now after this install, I get the selection screen & XP is listed there, but when I select it, I get "NTLDR is missing". If I go into the BIOS & boot to that drive first, XP will load just fine, so I know it is okay.

I need to know how to get Linux to allow me to dual boot as before. How do I configure this to work? I am sure it is an easy fix, but I am a linux noob, so I need your help!

Thanks in advance!

:)
GRUB needs a edit.
Go to Terminal and type in:```
sudo gedit /boot/grub/menu.lst
```
And tell us what it says!

---

### Post by discmaster on 2008-05-27
Wow, thanks for all the replies, everyone! I do remember doing this the last time for dual boot, but I am hesitant on making any changes when I don;t know what I am doing.

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
# kopt=root=UUID=96e11097-45ff-4a55-8d0a-bf08211a39e2 ro

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=96e11097-45ff-4a55-8d0a-bf08211a39e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=96e11097-45ff-4a55-8d0a-bf08211a39e2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
# on /dev/sdc1
title		Microsoft Windows XP Home Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


---

### Post by iaculallad on 2008-05-27
Try removing/commenting this

> map (hd0) (hd2)
map (hd2) (hd0)


from this, and do a restart:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title Microsoft Windows XP Home Edition
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

---

### Post by discmaster on 2008-05-27
Okay, here is what I changed it to, saved & rebooted. When I select Win XP to boot into, it goes to a black screen & says "starting up" & that's it. At least the "NTLDR is missing" is gone, but I still can't dual boot.

Here is the fdisk -l & menu lst; Did I miss something somewhere?

> tr@tr-desktop:~$ fdisk -l 
tr@tr-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=96e11097-45ff-4a55-8d0a-bf08211a39e2 ro

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=96e11097-45ff-4a55-8d0a-bf08211a39e2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=96e11097-45ff-4a55-8d0a-bf08211a39e2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
# on /dev/sdc1
title Microsoft Windows XP Home Edition
root (hd2,0)
savedefault
makeactive
chainloader +1



---

### Post by logos34 on 2008-05-27
You're still going to need those map lines--you're essentially [chainloading a windows drive in second position]("http://www.users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").  If you have only two hard disks, then windows should be:

> title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


---

### Post by Amstell on 2008-05-27
> **oedha said:**
> or supergrubdisk can also help :)

+1

SuperGRUB is great

[http://www.supergrubdisk.org](http://www.supergrubdisk.org)

Cheers

---

### Post by discmaster on 2008-05-27
> You're still going to need those map lines--you're essentially chainloading a windows drive in second position. 

Thank you, I got it working now. I will save this thread for future reference!

Again, thanks to all for replying!

:popcorn:

---

