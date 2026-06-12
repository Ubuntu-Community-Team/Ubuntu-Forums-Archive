---
title: "[SOLVED] Help!  My GRUB menu is filling up with old entries!"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by ionizd on 2008-07-29
I once had a dual-boot laptop that I decided to go Xubuntu-only.
 The entry is still on my boot menu, however, as well as every past linux core I've used.  How do I clean up the Grub boot menu?

---

### Post by eightmillion on 2008-07-29
Removing old kernels with synaptic will also remove them from the grub menu.

---

### Post by ace007 on 2008-07-29
OR:

```

sudo gedit /boot/grub/menu.lst

```

Scrool to bottom and remove unwanted entries.  (The kernels will still be there, they're not removed)

---

### Post by Potatoj316 on 2008-07-29
Like the above post said you can remove the old kernels and they will remove themselves from GRUB.  I would sugest leaving one old kernel, incase you have trouble with the current one.  As for the windows entry (i think you said that) you can edit the /boot/grub/menu.lst file.  Post it here and I can tell you what to take out

---

### Post by drs305 on 2008-07-29
In this case (removing a windows entry) it would be easiest just to open menu.lst and physically remove the windows items. Don't forget to back up the menu.lst first. This should be safe as long as the windows program is not the one started by default by menu.lst.
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksu gedit /boot/grub/menu.lst

```

For other tweaking of the grub menu, refer to the link about grub in my signature line. StartUp-Manager will help you tame grub's menu.lst without having to manually edit menu.lst.

---

### Post by LowSky on 2008-07-29
a programs called "start-up manager" can also safely remove those Kernels from appearing. Its in Add/Remove

---

### Post by ionizd on 2008-07-29
> **Potatoj316 said:**
> Like the above post said you can remove the old kernels and they will remove themselves from GRUB.  I would sugest leaving one old kernel, incase you have trouble with the current one.  As for the windows entry (i think you said that) you can edit the /boot/grub/menu.lst file.  Post it here and I can tell you what to take out


Here are the contents of that file;

[COLOR="Red"]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=871ae849-3a75-4d0b-938d-a4b1b47d985f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/COLOR]

---

### Post by drs305 on 2008-07-29
You could use StartUp-Manager to remove the old kernel references, however they would still remain on your computer. You can use StartUp-Manager to do this by changing the number of kernels to display. See link in signature.

A better solution would be to open synaptic, do a search for "linux-image" and then remove the older kernels from your computer. Removing them via synaptic will remove them from the boot menu as well. 

Keep the kernel you are currently using plus one older one you know works.

Current kernel:
```
uname -r
```

If you no longer have windows on this machine, you can open menu.lst (see earlier post) and remove this:
```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
__________________

```

---

### Post by fatality_uk on 2008-07-29
Just a thought!! If a kernel updates fails for instance, having the ability to roll back to a previous working kernel is a good thing ;)

---

### Post by Potatoj316 on 2008-07-29
you can safely get rid of thses lines (it will take windows out of the list)

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by ionizd on 2008-07-29
All done. I used Synaptic to remove the older Kernels, which removed them from the boot menu.  I was hesitant to do so until instructed as to which packages (Linux-image), but that worked swimmingly.  I left the last kernel intact for future use, per suggestions to do so.  I also removed the appropriate lines from the [COLOR="Red"]/boot/grub/menu.lst[/COLOR] file, which removed the windows entry.

 Thanks very much for the help.

---

### Post by alzie on 2008-07-29
> **ionizd said:**
> Here are the contents of that file;

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all





If you wish to edit your /boot/grub/menu.lst and change howmany from "all" to "2" then grub will only retain the last 2 entries.  Otherwise this will happen again as you receive more kernel updates. 

Personally I'd recommend using "startup manager" for this and set number of kernels to keep to 2.

I hope this helps

---

