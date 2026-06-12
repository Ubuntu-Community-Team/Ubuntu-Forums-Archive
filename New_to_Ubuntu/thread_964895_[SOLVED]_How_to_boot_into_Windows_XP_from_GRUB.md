---
title: "[SOLVED] How to boot into Windows XP from GRUB?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Tom--d on 2008-10-31
Hello,

at the moment I cannot boot into Windows XP through GRUB.

basically, what I have got is.

Xp on one Hard drive, Ubuntu on another. too separate drives.

I can boot into Ubuntu fine. but when booting into Windows XP, it just boots into GRUB again. Backing over its self.

I can boot into XP but pressing F11 at BIOS and changing the boot to the other hard drive. That works.

I want the Windows XP to work in GRUB.
here is my menu.lst
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
color white/black white/black

#A splash image for the menu
splashimage=/boot/grub/splashimages/grub-splash-dark.xpm.gz

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
# kopt=root=UUID=a0674f59-fe2d-426c-ae95-bad97216ea76 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a0674f59-fe2d-426c-ae95-bad97216ea76

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
# defoptions=quiet splash vga=795

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10
uuid		a0674f59-fe2d-426c-ae95-bad97216ea76
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a0674f59-fe2d-426c-ae95-bad97216ea76 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10 (recovery mode)
uuid		a0674f59-fe2d-426c-ae95-bad97216ea76
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=a0674f59-fe2d-426c-ae95-bad97216ea76 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		a0674f59-fe2d-426c-ae95-bad97216ea76
#kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1 (hd0,0)
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

```

Please help,

thanks.

---

### Post by Dr Small on 2008-10-31
Try changing:
```
root		(hd0,0)
```
To:
```
root		(hd0,1)
```

Since you said it is on the second hard drive.

---

### Post by Kevbert on 2008-10-31
Dr Small, don't you mean change it to 
```
root                 hd(1,0)
```
First number is hard disk (starting from 0), second number is partition (starting from 0).

---

### Post by ronnielsen1 on 2008-10-31
As Kevbert says, but don't you also have to map it?

root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by employeeno5 on 2008-10-31
> Dr Small, don't you mean change it to 
hd(1,0)



I agree, that's more likely to be correct. 

@Tom--d

What's happening here is that Grub is pointing to the wrong place.

Where it says hd(0,0) it's saying too look at the first hard drive (zero being the first count) and the first partition, which is where grub is located on your machine.

If you change it to hd(0,1) it's telling you to look at the same hard drive but the next partition. So it's hd("hard drive #","partition #")

So most likely you want hd(1,0) as you're then asking it to look at next hard drive and its first partition.

However, we don't know for sure how your computer is set up and partitioned. One way to do this is with trial and error.

There must a be a better way to do that though. Surely there must be a way to detect for sure how your windows partition is labeled but I don't know how to do that personally.

Maybe someone else can help you better, but know that you understand that basic scheme of things you might get it working with just one or two well chosen number schemes.

Oh, and you'll also need to make sure that,
```
chainloader +1
```
is listed in the line below you hd numbers for Windows.


Also, if I'm misinformed about any of that information please let me know. I'm no pro at this myself, but this is what's helped me on the GRUB front before.

---

### Post by Tom--d on 2008-10-31
Thank you for helping me but I still havent solved it.

I'm sure hd0 is my ubuntu Hard drive because when I boot into that, it goes back to GRUB.

What this map thing?
Should I do that?

also, I think the XP HDD is hd1. but im not sure. how can I find out?

---

### Post by click4851 on 2008-10-31
I fixed a similar setup using a SuperGRUB disk worked great and set GRUB up automatically to boot to either OS...give it a try.

---

### Post by Tom--d on 2008-10-31
> **ronnielsen1 said:**
> As Kevbert says, but don't you also have to map it?

root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

That worked!

Thanks :D

---

### Post by employeeno5 on 2008-10-31
That's great news Tom!

If you get this last post, you should go up to the top of this thread[s page where is says, "forum tools" and mark this thread solved. That way others with similar issues in the future will know they might find answers here, and others looking to help out will know you're already good.

Glad ronnielsen1 set things straight. Goodluck!

---

### Post by ronnielsen1 on 2008-10-31
> What this map thing?
Should I do that?
It makes Windows think it's running on the first hard drive

---

### Post by Tom--d on 2008-10-31
> **employeeno5 said:**
> That's great news Tom!

If you get this last post, you should go up to the top of this thread[s page where is says, "forum tools" and mark this thread solved. That way others with similar issues in the future will know they might find answers here, and others looking to help out will know you're already good.

Glad ronnielsen1 set things straight. Goodluck!

Done :)

---

