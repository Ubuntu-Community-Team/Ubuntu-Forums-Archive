---
title: "[SOLVED] noob having dual boot problems and grub menu problems"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by birchii on 2008-10-28
Hey, 

I had some problems with my grub menu, which i posted in the wrong place, so here is what i wrote
[http://ubuntuforums.org/showthread.php?t=961442]("http://ubuntuforums.org/showthread.php?t=961442")

so summing up, I have my grub menu now, but I am getting an error 22, and vista will not boot up at all now.

also i was reaing on the pro's and cons on whether or not to use 64 bit ubuntu. I would only be using my computer for everyday stuff, so is it worth me downloading 32 bit version and doing a complete re-install?

if someone can help me out i would be extremely gratefull

---

### Post by caljohnsmith on 2008-10-28
Based on your other post, it looks like you are booting from your Ubuntu drive on start up. Go ahead and reboot, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,4)" where X is a number, press "e" to edit it, change it to "root (hd0,4)", press return to save the change, then press "b" to boot. If that doesn't work, try (hd1,4). Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

If it doesn't work, then from your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu

```
If it does work though, you can open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And edit all the lines for Ubuntu to use the (hdX,4) that worked. See if you can get this far, or if not, let me know and we can work from wherever you are at. :)

---

### Post by birchii on 2008-10-28
I am typing on my newly installed ubuntu!!! boo-yeah
i edited it to hd(0,4). 
Thanks a lot!! Just need to save it.
Will check if i have problems with vista booting up.

---

### Post by birchii on 2008-10-28
this is what the saved version looks like now
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
# root		(hd0,4)
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
# kopt=root=UUID=5d77ae37-0dca-43f8-a421-e1f5896fd5d5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5d77ae37-0dca-43f8-a421-e1f5896fd5d5 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5d77ae37-0dca-43f8-a421-e1f5896fd5d5 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by birchii on 2008-10-28
All my ubuntu problems are solved now, but i still get the same error with trying to boot up vista...it says "bootmgr does not exist"

Any suggestions?

---

### Post by birchii on 2008-10-28
I played around a bit, using the logic from above posts and went into the grub menu highlighted vista and pressed 'e' and changed (hd1,0) to (hd0,0) so now instead of saying 'bootmgr" missing it nows says

Booting 'windows vista'
acpi
Vista Loader 2.0.0
Done!
Fallback 1
find --set-root /bootmgr

and just stays at this screen. What do i do?

---

### Post by wolfen69 on 2008-10-29
you will probably need to boot to the vista cd and choose repair. then fix your boot problem. but, you will also have to fix grub after that.

---

### Post by caljohnsmith on 2008-10-29
If Vista is on the same drive as Ubuntu, then you can use the following entry in your menu.lst to boot it:
```
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
makeactive
chainloader	+1
```
In other words, you don't need to use Grub's mapping technique if Vista is on the same drive. Try the above, and if you get any Vista errors on start up, let me know what they are and we can work from there. :)

---

### Post by Duck2006 on 2008-10-29
Delete the line

savedefault

As "caljohnsmith" posted if ubuntu is booted from the same drive ads vista, ie you only have one drive then the map lines are not needed.

Change the menu.lst from this,

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

To this,

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
makeactive

chainloader	+1

---

### Post by birchii on 2008-11-01
Thanks guys, 

Haven't been able to gt to the computer for a couple of days. Everything is working great :)

---

