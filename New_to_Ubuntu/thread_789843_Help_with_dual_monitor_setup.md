---
title: "Help with dual monitor setup"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by tsunamikitsune on 2008-05-10
I have two monitors connected to my computer: The first with VGA and the second with DVI. I'd like the first to have a resolution of 1280x1024 and the second 1440x900.

After some messing with the xorg settings and trying to set the correct resolutions, I had problems getting the first monitor to 1280x1024. I did get the second monitor to work at the correct resolution, but now the first is stuck at 640x480 and I can't move my mouse to the second screen.

I've obviously broken things pretty badly and it's difficult to fix things with such a low resolution, so I decided I should probably ask here for some help before making things worse.

Any suggestions?

---

### Post by warbread on 2008-05-10
What kind of video card do you have?  With Nvidia cards, this is nice and easy to set up.

---

### Post by Garyhans on 2008-05-10
I had this problem. I have Nvidia 6600 and Acer and Magnavox LCD. I reversed the hook up as to DVI VGA. Used EnvyNG. Then Sudo Nvidia-Settings after rebooting. It just wouldn't work hooked up the other way.

---

### Post by tsunamikitsune on 2008-05-10
I have an Nvidia GeForce 7300 GT for my video card. I tried to set things up in Nvidia-settings, but the correct resolution never shows up for the first monitor, even after going through the xorg settings.

---

### Post by warbread on 2008-05-10
Did you click on the "detect displays" button at the bottom?

I am kind of excited by the prospect of having to do this old school Hoary style, but feel sorry for you for having to do it.

---

### Post by Garyhans on 2008-05-10
How about NVidia-xconfig as root if your using Hardy.

---

### Post by tsunamikitsune on 2008-05-11
Seems I'm having a problem getting into Ubuntu altogether now.

When I reboot, my computer boots straight into Windows. The screen where I choose to start Ubuntu or Windows is gone.

I tried [this]("http://ubuntuforums.org/showthread.php?t=224351") twice and had no luck. Why is it missing?

---

### Post by warbread on 2008-05-11
Your Master Boot Record was over written.  I suggest installing [this in Windows]("http://www.fs-driver.org/") and then pulling out your /boot/grub/menu.list file and posting it here.

Did you, by chance, install Windows again?

---

### Post by tsunamikitsune on 2008-05-11
That's the strange thing, I haven't reinstalled Windows or done anything that would mess with the MBR as far as I know.

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
# kopt=root=UUID=50fe8e95-b9c0-4b89-bf94-78c2e99191ea ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=50fe8e95-b9c0-4b89-bf94-78c2e99191ea ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=50fe8e95-b9c0-4b89-bf94-78c2e99191ea ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=50fe8e95-b9c0-4b89-bf94-78c2e99191ea ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=50fe8e95-b9c0-4b89-bf94-78c2e99191ea ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



```

---

### Post by warbread on 2008-05-11
That is very odd.  You don't get the "Press ESC to enter Grub menu..." dialog at all?

The only thing I think it could be at this point is the map business on your XP entry.  Try commenting out both of the lines starting with 'map' and see if that helps.

Example:
#map		(hd0) (hd1)
#map		(hd1) (hd0)
If that screws anything up, at least it's easy to fix.

---

### Post by tsunamikitsune on 2008-05-11
Okay, I managed to get back into Ubuntu. The GRUB menu no longer shows up right away, but I hit ESC to bring up the "Boot Menu" when my screen showed the COMPAQ logo at startup. It let me choose which hard drive to boot from and when I choose the one with Ubuntu installed, the boot loader came up and allowed me to get in as usual. It seems as though GRUB has been installed on the slave hard drive (which has Ubuntu on it) rather than the master (the Windows hard drive). It should be on the Windows drive, shouldn't it?

Anyway, pressing ESC is a minor annoyance I can deal with for now. I'd really like to straighten out this resolution nonsense so I can actually navigate Ubuntu with some ease. I managed to bring up the Nvidia-settings and change the first monitor's resolution (which will only go to 1280x960 for whatever reason), but it wouldn't allow me to save the changes. Something about being unable to create a backup xorg.conf file.

Thank you for the help so far, hopefully you can help me get this straightened out. In typing this, my mouse pointer has somehow gotten stuck on the second monitor, while I can only navigate the first with my keyboard if I Alt-Tab to Firefox. This is very frustrating. XD

---

### Post by tsunamikitsune on 2008-05-11
Well, I've gotten the resolution problem worked out, at least to a workable degree. Still need to get things exactly the way I want them, but my biggest problem has been fixed.

---

### Post by warbread on 2008-05-11
> **tsunamikitsune said:**
> Okay, I managed to get back into Ubuntu. The GRUB menu no longer shows up right away, but I hit ESC to bring up the "Boot Menu" when my screen showed the COMPAQ logo at startup. It let me choose which hard drive to boot from and when I choose the one with Ubuntu installed, the boot loader came up and allowed me to get in as usual. It seems as though GRUB has been installed on the slave hard drive (which has Ubuntu on it) rather than the master (the Windows hard drive). It should be on the Windows drive, shouldn't it?



Oh!  I though you weren't even getting that.  You can fix that by commenting out the 'timeout' entry in your menu.list.  

```

#timeout		10


```

That should bring back the menu instead of having you press esc.  How did this change without you knowing?

---

### Post by warbread on 2008-05-11
> **tsunamikitsune said:**
> 

Anyway, pressing ESC is a minor annoyance I can deal with for now. I'd really like to straighten out this resolution nonsense so I can actually navigate Ubuntu with some ease. I managed to bring up the Nvidia-settings and change the first monitor's resolution (which will only go to 1280x960 for whatever reason), but it wouldn't allow me to save the changes. Something about being unable to create a backup xorg.conf file.


Try 

```

:-$ **sudo **nvidia-settings

```

It should allow you to save whatever changes you make.

---

