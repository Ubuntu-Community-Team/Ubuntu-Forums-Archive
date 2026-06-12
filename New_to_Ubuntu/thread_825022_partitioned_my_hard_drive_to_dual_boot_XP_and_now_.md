---
title: "partitioned my hard drive to dual boot XP and now going round in circles"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by jasonwatkins on 2008-06-10
ok, i followed the guide at apcmag to partition my hard drive - i've done it a few times before so I'm also fairly familiar with it.

i rebooted and loaded up gparted and resized off a 10gb chunk.

that went ok.

i installed and set up XP on that chunk - no problems.  Went back into gparted and made the linux partition the boot partition.

so i currently have :-

/dev/hdb1 - ntfs - Windows
/dev/hdb2 - ext3 - Linux - Boot

I rebooted and got the dreaded "error 17 - cannot mount partition".  so i tried using supergrub to fix things, but it didn't seem to have any effect.

i then rebooted, got the error and went into the command line and did

find /boot/grub/stage1

it returned (hd0,1)

so i then did

root (hd0,1)
kernel /vmlinuz root=/dev/ - and here i tried hda0,1,2,3 and 4 and all of them didn't work.

so i booted off the live CD and did 

sudo gedit

and edited the menu.list file in /boot/grub of my original linux partition.

i deleted everything and loaded the backup i'd taken, saved it and rebooted and STILL got the "error 17"

my output of fdisk -l is this

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x332eade2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406    7  HPFS/NTFS
/dev/sda2   *        1276       19080   143018662+  83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
```

my current menu.lst file is this ..

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(recovery mode) single
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

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

i'm just utterly stumped.  I went back to gparted and set the windows partition to be the boot partition and it didn't work - it still tried to boot into linux.

and i know it's linux mint, but the guts are still the same.

if anyone has any clues then i would be very, very grateful because i've totally run out of ideas - not that i'm a professed expert in this part anyway :)

---

### Post by barney385 on 2008-06-10
It looks to me like your \ and home/ext3 are backwards.

---

### Post by logos34 on 2008-06-10
you need to edit menu.lst--change 'groot' and 'root' lines to (hd0,1).  Also, kernel line 'root=/dev/sda2'

edit /etc/fstab to match (may nnot be necessary if using uuids).

Change boot flag (*) to windows sda1 with

sudo gparted

(manage flags option)

add windows entry to bottom of menu.lst:

> title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1

If still an error message, try (re)installing grub, but this time to the bootsector of the root partition:

sudo grub

> root (hd0,1)
> setup (hd0,1)
> quit

sometimes when you resize root (on the left border) if throws off grub

---

### Post by Oldsoldier2003 on 2008-06-10
> **jasonwatkins said:**
> ok, i followed the guide at apcmag to partition my hard drive - i've done it a few times before so I'm also fairly familiar with it.

i rebooted and loaded up gparted and resized off a 10gb chunk.

that went ok.

i installed and set up XP on that chunk - no problems.  Went back into gparted and made the linux partition the boot partition.

so i currently have :-

/dev/hdb1 - ntfs - Windows
/dev/hdb2 - ext3 - Linux - Boot

I rebooted and got the dreaded "error 17 - cannot mount partition".  so i tried using supergrub to fix things, but it didn't seem to have any effect.

i then rebooted, got the error and went into the command line and did

find /boot/grub/stage1

it returned (hd0,1)

so i then did

root (hd0,1)
kernel /vmlinuz root=/dev/ - and here i tried hda0,1,2,3 and 4 and all of them didn't work.

so i booted off the live CD and did 

sudo gedit

and edited the menu.list file in /boot/grub of my original linux partition.

i deleted everything and loaded the backup i'd taken, saved it and rebooted and STILL got the "error 17"

my output of fdisk -l is this

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x332eade2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406    7  HPFS/NTFS
/dev/sda2   *        1276       19080   143018662+  83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
```

my current menu.lst file is this ..

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(recovery mode) single
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

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

i'm just utterly stumped.  I went back to gparted and set the windows partition to be the boot partition and it didn't work - it still tried to boot into linux.

and i know it's linux mint, but the guts are still the same.

if anyone has any clues then i would be very, very grateful because i've totally run out of ideas - not that i'm a professed expert in this part anyway :)

try this
```
sudo grub
root (hd0,1)
setup (hd0)
quit
sudo reboot
```

---

### Post by jasonwatkins on 2008-06-10
thanks so much for your fast replies .. i will try each one out.

i only wanted to play Homeworld :D

---

### Post by jasonwatkins on 2008-06-10
> **logos34 said:**
> sometimes when you resize root (on the left border) if throws off grub

this appears to have worked - i have booted into my normal linux partition perfectly ok.

haven't yet booted to the XP partition but it should also be fine.

thankyou so much for saving me from killing my pc :D

and thanks everyone else for the suggestions.

---

### Post by jasonwatkins on 2008-07-07
> **logos34 said:**
> you need to edit menu.lst--change 'groot' and 'root' lines to (hd0,1).  Also, kernel line 'root=/dev/sda2'

edit /etc/fstab to match (may nnot be necessary if using uuids).

Change boot flag (*) to windows sda1 with

sudo gparted

(manage flags option)

add windows entry to bottom of menu.lst:



If still an error message, try (re)installing grub, but this time to the bootsector of the root partition:

sudo grub

> root (hd0,1)
> setup (hd0,1)
> quit

sometimes when you resize root (on the left border) if throws off grub

Thought i'd come back to this.  I had to re-format for various reasons and followed the above instructions to re-paritition again, but I had to reinstall grub onto the bootsector of the root partition because it flat out refused to load.

that fixed it, but whenever i rebooted and selected the XP partition, it then set that partition to be the boot partition.

so since i've reformatted, i have to re-load gparted every time to reset the boot partition back to the Linux one so it will give me the grub menu again.

i think i'm going to have to look at setting up an XP virtual box or VMWare installation really because I need it for a couple of things and i'm just having too much trouble with this partitioning business.

---

### Post by logos34 on 2008-07-07
> **jasonwatkins said:**
> had to re-format for various reasons and followed the above instructions to re-paritition again, but I had to reinstall grub onto the bootsector of the root partition because it flat out refused to load.

that fixed it, but whenever i rebooted and selected the XP partition, it then set that partition to be the boot partition.

so since i've reformatted, i have to re-load gparted every time to reset the boot partition back to the Linux one so it will give me the grub menu again.

Is linux root still sda2?

You should be getting the grub menu screen each time you boot...grub is your bootloader. not sure what you mean by 'reset the boot partition' ('*' boot flag?)

---

### Post by kansasnoob on 2008-07-07
Try installing startupmanager from synaptic.

Then go to System > Administartion > Start Up Manager and see if you can adjust what you want to adjust.

Beware ............ if you break it, you own it!

---

### Post by kansasnoob on 2008-07-07
"Is linux root still sda2?"

On who's drive?

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by logos34 on 2008-07-07
> **kansasnoob said:**
> "Is linux root still sda2?"

On who's drive?

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

I was referring to the fdisk from jasonwatkins initial post:

>  Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x332eade2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406    7  HPFS/NTFS
[COLOR=Blue]/dev/sda2   *        1276       19080   143018662+  83  Linux[/COLOR]
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5 19081 19457 3028221 82 Linux swap / SolarisJust wondering if he didn't change it with all the reformatting, repartitioning and whatnot (in which case 'root (hd0,1)' would no longer work).  I guess he reinstalled:
> I had to re-format for various reasons and followed the above instructions to re-paritition again...

Apparently root is still the same upon rereading what he says:

> , but I had to reinstall grub onto the bootsector of the root partition because it flat out refused to load.
 
 that fixed it, but whenever i rebooted and selected the XP partition, it then set that partition to be the boot partition.
 
 so since i've reformatted, i have to re-load gparted every time to reset the boot partition back to the Linux one so it will give me the grub menu again.

But I'm having a hard time figuring out why the grub menu doesn't appear until he sets the boot flag to linux root (normally linux could care less about it--windows is more finicky about that).  Windows apparently keeps setting it back, probably because of the 'makeactive' option in the xp menu.lst entry

---

### Post by jasonwatkins on 2008-07-08
ok, installed startup manager but it won't run.  i click on it and nothing happens.

by "reset the boot partition" i mean that whenever I boot into windows, it then *always* boots into windows.  i re-load gparted and the windows partition is now set to the boot partition, and i have to reset it back to the linux partition to get the grub menu back up.

my current fdisk -l is ..

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x332eade2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        2551       19080   132777225   83  Linux
/dev/sda3           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris
```

my current menu.lst is .. 

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

gfxmenu=/etc/grub/message.elyssa

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda1 ro

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
##      altoptions=(recovery mode) single
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

title		Linux Mint, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Linux Mint, kernel memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

title Windows XP
root (hd0,0)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```

i guess it's fairly obvious i'm using linux mint, but the guts are the same and you guys in this forum are better than the ones on theirs :D

---

### Post by bumanie on 2008-07-08
You should have this line in between the end of the ubuntu  entries and the windows entry.>  # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1 So that it looks like this

> ### END DEBIAN AUTOMAGIC KERNELS LIST

[COLOR="Red"]# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root[/COLOR]


[COLOR="Red"][COLOR="Black"][COLOR="Red"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1[/COLOR][/COLOR][/COLOR]
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[COLOR="Black"]You need to add the parts in red[/COLOR]

---

### Post by jasonwatkins on 2008-07-08
> **bumanie said:**
> You should have this line in between the end of the ubuntu  entries and the windows entry. So that it looks like this

I've done this but it makes no difference - i booted to windows and it "grabbed" the boot flag to make itself the boot partition again.

i had to re-load gparted and re-set the boot partition to the linux partition.

---

### Post by logos34 on 2008-07-08
> **jasonwatkins said:**
> ok, installed startup manager but it won't run.  i click on it and nothing happens.

by "reset the boot partition" i mean that whenever I boot into windows, it then *always* boots into windows.  i re-load gparted and the windows partition is now set to the boot partition, and i have to reset it back to the linux partition to get the grub menu back up.


> i booted to windows and it "grabbed" the boot flag to make itself the boot partition again.

i had to re-load gparted and re-set the boot partition to the linux partition.I thought that's what you meant--it changed the boot flag.  As I said, though, linux root/boot partition normally doesn't care about boot flag, so I'm not sure why you need to put it back in order to get grub to appear.

First, clean up a couple of items in menu.lst:

> # kopt=root=/dev/sda[COLOR=Blue]**2**[/COLOR] ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,[COLOR=Blue]**1**[/COLOR])
Also, this line:

> gfxmenu=/etc/grub/message.elyssaDid it get added when you ran Startup-manager?  If not, maybe the settings in that file are conflicting

As far as it always defaulting to XP after you boot into the latter, it's usually because of 'default saved' line, but I see yours is set the ' default 0' (meaning it should boot the first linux mint kernel).  Just for good measure, though, you might want to remove the 'savedefault' line from windows entry.

Try reinstalling Grub to the MBR _AND_ the boot sector of sda2, linux root.

> sudo grub

grub> root (hd0,1)
grub> setup (hd0)
grub> quit> sudo grub

grub> root (hd0,1)
grub> setup (hd0**,1**)
grub> quit
Give that a shot.

---

### Post by jasonwatkins on 2008-07-08
> **logos34 said:**
> Give that a shot.

It now does appear to be working again so I must thank you most profusely :)

---

### Post by logos34 on 2008-07-08
ok, good to hear things are back to normal.

Enjoy!

---

