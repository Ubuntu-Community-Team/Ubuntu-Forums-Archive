---
title: "[SOLVED] help with dual boot."
date: 2008-05-27
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-05-27
I had ubuntu installed by itself and recently set aside a partition for windows, i installed windows on that partition, but it appears to have either written over or it starts before the Grub bootloader.. so it will now boot strait into windows without giving me an option to select an OS.. 

I can get into ubuntu only through the live CD.... what can i do to get my grub back?

---

### Post by sayakb on 2008-05-27
Check out Super Grub disk:
[www.supergrubdisk.org/](www.supergrubdisk.org/)

Documentation: [www.supergrubdisk.org/wiki/SuperGrubDisk](www.supergrubdisk.org/wiki/SuperGrubDisk)

---

### Post by Duck2006 on 2008-05-27
Boot the live cd of ubuntu. Open the terminal and type

sudo grub

find /boot/grub/stage1
It will come back with some thing like (hd0,2)

root (hdx,y)
use the output that the find came back with

setup (hd0)

quit

some reading on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by rabidninjawombat on 2008-05-27
> **LinuxIsInnovation said:**
> Check out Super Grub disk:
[www.supergrubdisk.org/](www.supergrubdisk.org/)

Documentation: [www.supergrubdisk.org/wiki/SuperGrubDisk](www.supergrubdisk.org/wiki/SuperGrubDisk)

as a matter of fact, i remember burning that disk, and completly forgot about it.. im an idiot :)  thanks!

---

### Post by Paqman on 2008-05-27
> **rabidninjawombat said:**
> what can i do to get my grub back?

You need to [restore Grub](http://ubuntuforums.org/showpost.php?p=117829&postcount=2)

---

### Post by sayakb on 2008-05-27
If you have no further queries, please mark the thread as solved :)

---

### Post by rabidninjawombat on 2008-05-27
Ok grub is restored. easy peasy. I am missing windows XP from the grub list.  I am attempting to add it to the grub boot loader, and running into some errors.  (error code 13 to be specific. 

This is what i added per some searching and research 

```
title           Microsoft Windows XP Professional
root            (hd1,1)
savedefault
makeactive
chainloader     +1

```

This was added after the 

```
### END DEBIAN AUTOMAGIC KERNELS LIST
``` btw in the /boot/grub/menu.lst file. 

Where i think im having the problem is in the area 
```
root            (hd1,1)
```

Im assuming its not refering to the proper area?

Windows is installed on the slave hard drive, on the second partition.

---

### Post by Duck2006 on 2008-05-27
In the terminal run

cat /boot/grub/menu.lst

and

sudo fdisk -l

and post the outputs

---

### Post by rabidninjawombat on 2008-05-27
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
# kopt=root=UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 ro

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

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd1,1)
savedefault
makeactive
chainloader     +1

```

```

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x13981398

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2429    19510911   83  Linux
/dev/sda2   *        2430        4997    20627460    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x036066f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9352    75119908+  83  Linux
/dev/sdb2            9353        9729     3028252+   5  Extended
/dev/sdb5            9353        9729     3028221   82  Linux swap / Solaris

```

---

### Post by rabidninjawombat on 2008-05-27
actually i think i see my problem correct me if im wrong.. looks like my windows partition is actually on my first HD rather then my slave,  been a while since ive used this PC. 

So there form the location should point toward (0,1)?

---

### Post by kansasnoob on 2008-05-27
So, you have two hard drives ........ XP on one drive while Ubuntu is on the other?

We need to know that.

---

### Post by Duck2006 on 2008-05-27
Add these lines to your menu.lst

map (hd0) (hd1)
map (hd1) hd(0)

so your windoze looks like this.

title           Microsoft Windows XP Professional
root            (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

---

### Post by rabidninjawombat on 2008-05-27
> **Duck2006 said:**
> Add these lines to your menu.lst

map (hd0) (hd1)
map (hd1) hd(0)

so your windoze looks like this.

title           Microsoft Windows XP Professional
root            (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

Got it. 

i currently have 

put that in and tried it before i read your post. :) 

```

title           Microsoft Windows XP Professional
root            (hd1,1)
savedefault
makeactive
chainloader     +1

```

in the menu.lst file and it works perfectly. 


What function does the 
```

map (hd0) (hd1)
map (hd1) (hd0)

``` 

serve? and should i have it in there even though its working?

---

### Post by rjdsmiths on 2008-05-27
You just need to install the GRUB bootloader into the MBR of your drive.

With the live Ubuntu cd.

When you get to the desktop open a terminal and enter.

sudo grub

This will put you into a "grub>" shell (i.e. the grub prompt). At grub>. enter these commands

grub >find /boot/grub/stage1

Whatever was returned for the find command use it in the next step (you are still at grub>.

grub >root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,2) then you would enter root (hd0,2)

Next enter the command to install grub to the mbr

grub >setup (hd0)

Then exit the grub shell

grub> quit

Then reboot without the CD.

Hope this helps.....

[Credit to cdtech]

---

### Post by Duck2006 on 2008-05-27
> What function does the
Code:

map (hd0) (hd1)
map (hd1) (hd0)

serve? and should i have it in there even though its working?

That just changes the drives around ie hd0 becomes hd1 and hd1 becomes hd0
You only use it if the win drive isn't the first boot drive.

---

### Post by rabidninjawombat on 2008-05-27
Ahh cool. thanks.. and as i found earlier it is so guess i dont need it :) 

thanks so much for the help. marking solved.

---

