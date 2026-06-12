---
title: "Problems loading ubuntu after the power is turned off"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by morph2386 on 2008-07-18
Hi,

I'm very new to Ubuntu so if I don't add enough information here apologies.
I have installed Ubuntu on an old laptop and it works perfectly once I have logged in and it is up and running. The problem is that when the power is turned off and turned back on again, it will go past the GRUB loading screen, gets to the screen that says starting up and then I get a blank screen. The keyboard won't respond and I cannot use Ctrl Alt and F1. I also searched the forums for similar problems and tried adding acpi = off to the GRUB command line but this made no difference.
It will load as normal though if I press Esc to enter the GRUB menu when it is loading and press Enter to choose the first partition.

I have tried to search for a fix for this but have had no luck. Please help.

Many thanks

---

### Post by NilsE on 2008-07-18
When it does come up look in your /boot/grub/menu.lst and make sure the kernel entry you are selecting when you do the esc selection is set as the default boot image. The line you are looking for is

default		0

the 0 equals the first kernel entry, 1 is second etc..

Also, how long are you waiting at the blank screen?  It may be doing a disk check which takes awhile and if quiet is set in the startup manager you will not see it.

---

### Post by morph2386 on 2008-07-18
I have checked /boot/grub/menu.lst and the line you mentioned is set to default 0
I have left the blank screen for 2 hours before now and it is still just showing a blank screen.
Hope this helps.

---

### Post by morph2386 on 2008-07-21
Hi, can anyone help please?

---

### Post by coffeecat on 2008-07-21
Have I got this right? If you switch on and let grub boot up the default, that is when you get the blank screen? But if you press escape and choose the first grub menu entry, then it will boot up properly?

That's odd.

I suggest you post the whole of your /boot/grub/menu.lst, then perhaps we can see what's wrong.

---

### Post by morph2386 on 2008-07-22
If I go into the grub menu and press enter on the first option it will load ok but if I don't and let it boot normally it gets past the grub menu screen, says "Starting up, loading" goes to the Ubuntu loading screen and then goes blank. 

Anyway, the text from /boot/grub/menu.lst

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
# kopt=root=UUID=3836b8b5-50ab-47da-ad06-6de36ae597aa ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3836b8b5-50ab-47da-ad06-6de36ae597aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3836b8b5-50ab-47da-ad06-6de36ae597aa ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3836b8b5-50ab-47da-ad06-6de36ae597aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3836b8b5-50ab-47da-ad06-6de36ae597aa ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by coffeecat on 2008-07-22
Thanks for explaining again. It needed clarifying because that's what I understood from the thread and...

> **coffeecat said:**
> That's odd.

I think I need to rephrase that; that's extremely odd, because....

> **coffeecat said:**
> ...perhaps we can see what's wrong.

I can't see anything wrong at all. :?

When you choose the first option from the menu, you are booting up from this stanza:

```
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=3836b8b5-50ab-47da-ad06-6de36ae597aa ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet
```And if you let it boot up from the default (0) it uses the same stanza. :-k

Can anyone else see anything I'm missing?

**morph2386**, the only thing I can suggest it to edit menu.lst so that the line:

```
hiddenmenu
```becomes

```
#hiddenmenu
```This means that you don't have to press esc each time - a bit more convenient. There's a 3 second timeout before it boots up. If you want to make that longer, edit:

```
timeout              3
```to whatever you want, 5, 10, whatever.

That's not going to fix this, but at least you'll get to see what's going on when it boots from the default. Perhaps you'll get to see some message that's not showing for some reason.

---

### Post by morph2386 on 2008-07-26
**morph2386**, the only thing I can suggest it to edit menu.lst so that the line:

```
hiddenmenu
```becomes

```
#hiddenmenu
```This means that you don't have to press esc each time - a bit more convenient. There's a 3 second timeout before it boots up. If you want to make that longer, edit:

```
timeout              3
```to whatever you want, 5, 10, whatever.

That's not going to fix this, but at least you'll get to see what's going on when it boots from the default. Perhaps you'll get to see some message that's not showing for some reason.[/QUOTE]


Thanks, that has made life easier,there's nothing else that is showing though that is any different from before.

---

### Post by eightmillion on 2008-07-26
morph2386, can you post the output of "ls -l /boot"?

---

### Post by morph2386 on 2008-07-26
I think this is what you were after:

```
sam@sam-laptop:/boot$ ls -l
total 36200
-rw-r--r-- 1 root root  422607 2008-04-10 17:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root  422667 2008-07-12 06:30 abi-2.6.24-19-generic
-rw-r--r-- 1 root root   79964 2008-04-10 17:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root   80049 2008-07-12 06:30 config-2.6.24-19-generic
drwxr-xr-x 2 root root    4096 2008-07-26 09:42 grub
-rw-r--r-- 1 root root 7884452 2008-07-09 19:00 initrd.img-2.6.24-16-generic
-rw-r--r-- 1 root root 7349268 2008-04-22 19:00 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root 7491227 2008-07-16 21:41 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7491486 2008-07-14 22:20 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 11:06 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 17:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root  905170 2008-07-12 06:30 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 17:51 vmlinuz-2.6.24-16-generic
-rw-r--r-- 1 root root 1921432 2008-07-12 06:30 vmlinuz-2.6.24-19-generic

```

Let me know if not

Cheers

---

