---
title: "Ubuntu as Default?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by SLaCK3r on 2008-04-28
OK, So I have Ubuntu 8.04 installed. Everything is running smooth. A little while ago I tried to completely deleted windows, but I must've accidentally deleted some Ubuntu Files. So I reinstalled. So when I boot up i get the option to boot with Vista or Ubuntu. I want Ubuntu to automatically start up. How can I do this?

---

### Post by LaRoza on 2008-04-28
> **SLaCK3r said:**
> OK, So I have Ubuntu 8.04 installed. Everything is running smooth. A little while ago I tried to completely deleted windows, but I must've accidentally deleted some Ubuntu Files. So I reinstalled. So when I boot up i get the option to boot with Vista or Ubuntu. I want Ubuntu to automatically start up. How can I do this?

Wait the 10 seconds?

You can reduce that time by editing /boot/grub/menu.lst and changing:

```

timeout		10

```

---

### Post by dokdoom on 2008-04-28
When you reinstalled, during the partition setup did you delete the original partitions?

---

### Post by Tatty on 2008-04-28
post your /boot/grub/menu.lst

---

### Post by SLaCK3r on 2008-04-28
> **dokdoom said:**
> When you reinstalled, during the partition setup did you delete the original partitions?

Well, #1, this would be easier if I could tell which drive was my C:\ and my D:\ 


And it never had a partition setup. I used the internet download and used Wubi.exe.


EDIT Boot/GRUB/Menu.lst

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
# kopt=root=UUID=3ADE7C14DE7BC6A3 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)/ubuntu/disks

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
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3ADE7C14DE7BC6A3 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3ADE7C14DE7BC6A3 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)/ubuntu/disks
kernel		/boot/memtest86+.bin

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
chainloader	+1

```

---

### Post by LaRoza on 2008-04-28
> **SLaCK3r said:**
> Well, #1, this would be easier if I could tell which drive was my C:\ and my D:\ 


And it never had a partition setup. I used the internet download and used Wubi.exe.

I am not sure about Wubi.

There is no C: or D: in Linux. That is an ancient scheme of a pre DOS OS called CP/M. (C: is for CP/M ;))

---

### Post by elmer_42 on 2008-04-28
First, I would reccomend backing up the file we are about to edit.
```
sudo cp /boot/grub/menu.lst ~/grub_menu.bak
```
Then, open up a terminal and run this:
```
sudo gedit /boot/grub/menu.lst
```
Then scroll down to where it says "timeout		10". Just change the 10 to however many seconds you want it to take before automatically booting. Save the file and you are done! Note, if you hosed your menu.lst, you can restore it with this command.
```
sudo cp ~/grub_menu.bak /boot/grub/menu.lst
```

---

### Post by SLaCK3r on 2008-04-28
Ok, thanks. Will this automatically make Ubuntu boot? Or the selected option? Because vista is the option that is automatically selected when I boot. I have to use my arrow keys to select one.

---

### Post by motang on 2008-04-28
> **SLaCK3r said:**
> OK, So I have Ubuntu 8.04 installed. Everything is running smooth. A little while ago I tried to completely deleted windows, but I must've accidentally deleted some Ubuntu Files. So I reinstalled. So when I boot up i get the option to boot with Vista or Ubuntu. I want Ubuntu to automatically start up. How can I do this?
Well the easiest way to do this is to install a program called **Startup Manager**.  Go to Applications -> Add and Remove and search for Startup Manager. After you install it, launch the program which is found in System -> Administration.  The fist tab is Boot Options and under Misc. uncheck _Show Bootloader Menu_.  That should do the trick and Timeout in second to **0**.  Hope this helps you out.

---

### Post by elmer_42 on 2008-04-28
If you follow my short guide up there, just change timeout to 1. It will wait one second, but one second is short enough, right? I have never tried changing it to 0, but if you want to try it, make sure you back up your menu.lst before you try. I would assume it just doesn't wait at all, but I don't want to screw around with things that I don't need to screw around with.

---

### Post by SLaCK3r on 2008-04-29
Well, see, I dunno if this will make Ubuntu run automatically because Windows is the one selected. Will that let me use Ubuntu as default?

---

### Post by joshsmith on 2008-04-29
hey, did you use wubi, if you did the windows bootloader goes before grub (the ubuntu one), so you need to change order in the windows bootloader

in windows xp at least you can do this in the file
c:\boot.ini
or for a graphical method 
control panel >system>advanced >startup (or something like that)

---

### Post by joshsmith on 2008-04-29
alternatively if you want the ubuntu bootloader in charge, you can look at

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

grub is good.

---

