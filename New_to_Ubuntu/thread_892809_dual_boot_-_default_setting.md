---
title: "dual boot - default setting"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Dr Noam on 2008-08-17
Yet another dual boot question... 

My dual boot XP/ubuntu works fine. Windows is the default (ie, first on the menu at startup, and if I turn on the computer and don't wait for the menu it will go into Windows automatically) and I want to make ubuntu the default. Can anyone tell me how to change this?

Thanks,
Noam

---

### Post by GreenN00b on 2008-08-17
You need to edit /boot/grub/menu.lst and set "default" option to the system you want to boot. The "default" option should be close to the beginning of this file.

---

### Post by Elfy on 2008-08-17
Edit the file and change the default number - count down the numbers of 'title' from 0 - example - to boot last ubuntu would have default 2

> title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=ccf8f1c4-97d0-4544-a0ee-04088d5d67a9 ro quiet vga=771 splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by kool_kat_os on 2008-08-17
Just post your /boot/grub/menu.lst contents here and we will tell you what to set the default to

---

### Post by Dr Noam on 2008-08-17
Sorry Forestpixie, didn't understand what you meant. My menu.lst is:

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
# kopt=root=UUID=CA5862FB5862E5A3 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=CA5862FB5862E5A3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=CA5862FB5862E5A3 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1

---

### Post by kansasnoob on 2008-08-17
The simplest and safest way to deal with this is by installing startupmanager:

[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

---

### Post by GreenN00b on 2008-08-17
Yes, startupmanager is a good solution and it is in the synaptic package manager too so you can easily install it from there.

However I have a question here, as I look at the menu.lst file I see the default is set to 0, why is not booting Ubuntu then ??

---

### Post by kool_kat_os on 2008-08-17
EDIT: when you see ubuntu on the list when grub loads...which line is it on?

---

### Post by Elfy on 2008-08-17
Is this wubi? If it is then you need to read the boot link below - and alos make sure that you tell people that it's wubi when you post threads - sometimes it can make a difference to the answers.

This is the wiki for it [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

For booting ubuntuas default 
[https://wiki.ubuntu.com/WubiGuide#How](https://wiki.ubuntu.com/WubiGuide#How) do I make Ubuntu the default boot option?

---

### Post by Dr Noam on 2008-08-17
Yes, it is wubi. Didn't realise that made a difference. Thanks for the tip, it tells me (in case others are interested): > Ubuntu is not installed as the default boot option, you have to select it in the windows boot menu. To change that, in windows XP go to control_panel > system > advanced > startup_and_recovery and edit the "Default Operating System", if you want you can change the timeout as well.

---

### Post by kool_kat_os on 2008-08-17
> **Dr Noam said:**
> Yes, it is wubi. Didn't realise that made a difference. Thanks for the tip, it tells me (in case others are interested):

i guess we should of all asked that question first...:)

---

### Post by Elfy on 2008-08-17
When you're done can you mark thread solved please.

TBH I only asked because the menu list was pointing at an odd place. Hopefully you'll be able to get it sorted now, if in the future you decide to make your wubi a 'real' dualboot - the information to do so is on the wiki.

---

### Post by Elfy on 2008-08-17
> i guess we should of all asked that question first...Don't agree with that it's much more fun to wait for it to magically appear lol

---

