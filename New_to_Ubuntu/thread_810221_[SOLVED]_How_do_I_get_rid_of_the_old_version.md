---
title: "[SOLVED] How do I get rid of the old version?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by bobmac on 2008-05-28
Folks,
After much ado I managed to install version 8.04 from a cd that I received from ubuntu. What I really wanted to do was upgrade from version 7.10 but is seems that the cd is only good for installing a totally new version. Which means that I've now got 2 version. I posted a query on the installation forum which told me that what I needed was to download a 'cd' and use it and delete the partitions using the Gnome Partition Editor. I duly downloaded the editor and deleted the partitions with disasterous results. It would appear that I deleted the wrong partitions. As my machine also has Windows XP pro I then tried to start my machine with it. No go! all I got was an error 22 message. The end result is that I've had to reinstall Windows and version 8.04. However, the version 7.10 that I originally tried to delete is still there and working.
Does anyone know how I can remove just version 7.10 while keeping my XP and version 8.04 intact.

I managed to take a screen shot of the Gnome Partition Editor as things now stand which I've attached.

Any assistance will be gratefully appreciated

Bob

---

### Post by tk03759 on 2008-05-28
Well for future reference, to do the update from the cd, you could have logged into ubuntu and inserted the 8.04 cd while in the version you wanted to upgrade. As far as I know and have tried, ubuntu would have asked you if you wanted to install the packages found on the cd, which would have upgrade your system.


As for your problem now, which os did you use to take that screenshot? Ubuntu 8.04, 7.10, or the live cd?

---

### Post by iaculallad on 2008-05-28
To remove your 7.10 partition without incurring a mistake again, post your /boot/grub/menu.lst (**cat /boot/grub/menu.lst**) so we could figure out of what partition Gutsy resides.

---

### Post by Oldsoldier2003 on 2008-05-28
From looking at your screenshot hda3 is the old version of Ubuntu, since its not mounted. The partition with your currently running version would be "locked" so you can delete /dev/hda3 then remove any references to it from your /boot/grub/menu.lst

You can reformat the partition and use it for extra storage, just add it to your fstab.

---

### Post by tk03759 on 2008-05-28
Actually, it doesn't matter. What I meant to ask was can you boot into the 8.04 installation?

If so, you're going to want to open a terminal and type

```
sudo apt-get install gparted
```

and then type gparted in the terminal to run gparted. Select the partition that 7.10 is installed to, and delete it. Then resize the 8.04 partition to the new desired size if you'd like, and apply the changes.

---

### Post by Oldsoldier2003 on 2008-05-28
> **tk03759 said:**
> Well for future reference, to do the update from the cd, you could have logged into ubuntu and inserted the 8.04 cd while in the version you wanted to upgrade. As far as I know and have tried, ubuntu would have asked you if you wanted to install the packages found on the cd, which would have upgrade your system.


As for your problem now, which os did you use to take that screenshot? Ubuntu 8.04, 7.10, or the live cd?

you have to use the alternate installer to do an upgrade IIRC

---

### Post by tk03759 on 2008-05-28
> **Oldsoldier2003 said:**
> you have to use the alternate installer to do an upgrade IIRC

Thank you, my bad.

---

### Post by linuxnewbie27 on 2008-05-28
Hi
 I am just curious can you boot into 7.10? If you can then why not delete 8.04 partition and upgrade in the ways suggested by posters above? Thats what you originally wanted right? , an upgrade to preserve your old setting?

---

### Post by bobmac on 2008-05-28
iaculallad,
Many thanks for your reply. Here is my boot/grub/menu.lst file

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
# kopt=root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by sayakb on 2008-05-28
If you have 7.10 on a separate partition and that is still operational, insert the 8.04 LiveCD and delete the 7.10 partition and remove it's entry from /boot/grub/menu.lst

---

### Post by iaculallad on 2008-05-28
> **bobmac said:**
> iaculallad,
Many thanks for your reply. Here is my boot/grub/menu.lst file

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
# kopt=root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0087f0b9-d77a-4369-a61d-c724d7af449a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a315c84-5f08-490c-9316-d5b282781dc4 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		Ubuntu 7.10, memtest86+ (on /dev/hda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

Hda3 is where you're Gutsy reside. Refer to your gparted picture and try to delete it. Then you can remove any traces of Gutsy on your /boot/grub/menu.lst. (I assume that you're booting now on you're 8.04 OS)

---

### Post by sayakb on 2008-05-28
Delete all the entries that comes after the line: chainloader +1
That would remove all instances of Gutsy from the menu. Now delete the partition using the Hardy/Gutsy liveCD

---

### Post by bobmac on 2008-05-29
Folks,

I've noted all of the replies to my posting but am still in the dark. My problem is that I seem to have somehow installed the new version (8.04) at least twice.

This has probably occurred because I have inserted the new cd more than once and simply followed what appeared to be the most obvious menu option (install).

I have also noted one reply that told me to delete part of the /boot/grub/menu.lst file, which I eventually located. However, when I attempt to do this, the text editor option under the Applications menu item informs me that I do not have permission to perform a save operation after attempting to perform the deletion.

In addition, the same reply that discusses deleting part of the /boot/grub/menu.lst file mentions that when I've completed the deletion I can then delete the offending partition.

Therein lies the problem. Which partition do I delete, there appears to be several. This was my original problem as can be seen from my original posting.

Perhaps one of the many gurus can explain exactly how I can get out of my dilemma in words that a absolute beginner can understand.

Any assistance will be gratefully accepted.

Regards,

Bob

---

### Post by forestpixie on 2008-05-29
Hi - first - boot menu, it has to be opened with root rights so that you can save any changes.

```
gksudo gedit /boot/grub/menu.lst
```

The old 7.10 installation is on hda3 - it tells you that in your menu.lst - use gparted to format it to ext3, you also have a spare swap - see your gparted - hda5 is not mounted and is not being used.

---

### Post by bobmac on 2008-05-29
Many thanks to all that replied to my query.

---

