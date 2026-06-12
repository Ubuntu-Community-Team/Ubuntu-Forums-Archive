---
title: "[SOLVED] Grub confused"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by phread59 on 2008-05-11
I have a dual boot set up right now.  I have XP Pro 64 bit on a Sata II hard drive.  Ubuntu is on an IDE drive on the primary channel set up as master.  I added a second IDE drive yesterday.  I want to put 64 bit Ubuntu on it.  Anyway I tried to boot into XP this afternoon and I got an Error5 partiton error coming back from Grub.  I think Grub is going to the second hard drive and finding nothing on it because it is new and I didn't load anything on it yet.  How Do I reset Grub to look for the second and third drives?

Mark Shuman

---

### Post by annda on 2008-05-11
i think you are right and probably the new drive uses the xp disk's address. first try

```
sudo update-grub
```

this should fix the problem. if not, please post the contents of your /boot/grub/menu.lst file and the output of 

```
sudo fdisk -l
```

---

### Post by morgan141 on 2008-05-11
Run the command from the terminal:
```
sudo gedit /boot/grub/menu.lst
```

From there scroll down to a bit that looks like:

```

title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
```
It won't necessarily look quite like that but you should be able to recognise it. It is essentially the windows part of the grub file.

Now it's the line 'rootnoverify (hd0,0)' that we're interested in. The numbers in the (hd0,0) bit represent the hard drive number and the partition number respectively. Since you've added a hard drive the hard drive number has changed, so add 1 to the first number. So for example if it was originally (hd1,1) then change it to (hd2,1).

Save and reboot :). If it doesn't work you can try other numbers but it'll never be higher than the number of hard drives you have.

edit: After a quick read of the man page it appears the annda's solution is easier and more straightforward so have a go at that first :)

---

### Post by phread59 on 2008-05-11
Hey Morgan thank you very much.  I went into the Grub list and changed the root and the mapping numbers from 1 to 2 and here I am back in Windydoze.  All is almost well.  I gotta laugh though.  Staples had Microsoft chordless keyboards and mouse sets on sale for 30$ this week so I ran out and bought one.  I hooked it up and all is well with Ubuntu.  It just kept on goin'. Didn't have to do a thing.  Went from a standard keyboard to an extended without changing anything at all.

Today I just logged in to Windughs and the cursor is locked.  Keyboard is dead.  Oh crap I think what did I do now?  I then remembered, hows about running the set-up disc.  Now it works.  Go figure Microsoft the software won't recogize Microsoft the hardware.  Now I know why I love Linux so much.  Stupid Gates products.

I want to add a coupla distros on the now #2 drive.  Will I have to add the drive and map it like I did for  the original drive?  I'm in Windows now so I can't post Grub listings.  But I basicly changed root from (0,0) to (1,0).  Added a comand to makeit go (I forgot the exact wording) Then added 2 map commands mapping (1,0) and (O,1).  I got it from a post here andd it has worked fine.  I also added a line to tell grub what the other op system was.  Any thoughts?

Mark Shuman

---

### Post by morgan141 on 2008-05-11
No problem :)

I'm not sure what you mean, have you got a link to the post? When you get back into linux can you post up your /boot/grub/menu.lst as well? Cheers.

The method I use when dealing with several distros is to firstly backup your current menu.lst file. After the install let it the distro wipe the mbr and to create it's own grub file. After that boot into the distro and add to the bottom of the menu.lst the entries for you current linux and windows os's and save. They should be all there after a reboot.

The only problem with this is if you decide to remove the second distro you need to restore the grub file from the first distro. There are howtos that tell you how to do this better than I can so I'll quickly have a look for one.

edit: [here's one](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub) :)

---

### Post by phread59 on 2008-05-12
:# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=6d9634da-bbb0-4055-b4fb-da2eefb72e4a ro

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
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6d9634da-bbb0-4055-b4fb-da2eefb72e4a ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6d9634da-bbb0-4055-b4fb-da2eefb72e4a ro single
initrd		/boot/initrd.img-2.6.24-16-generic

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
# on /dev/sdb1
title		Windows XP Professional x64 Edition
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

This is my grub list as requested.  I figure I will have to set it up just like above with a new entry for 64 Ubuntu and Fedora with (hd1,0) in root and mapping as above.  Am I wrong here?  Any help would be appreciated.

Mark Shuman

---

### Post by phread59 on 2008-05-12
Lordy do I have it messed up now.  I somehow ended up deleting Grub's list.  Couldn't get it back.  Grub died and now I cannot get it to work again.  I removed the new drive, reinstalled Ubuntu to get Grub back.  Reentered my grub settings and now I cannot get Windows back.  If I remove the new drive and reset to the original settings in the list it comes back with "Eror 11 unrecognized device string".  With all 3 drives hooked up and resetting it to what you see gives me "error 23 error while parsing number"  I have tried all kinds of configurations and have failed miserably.  I'm very tired and heading to bed.  Any suggestions on how to fix this.  I think I cut and pasted my grub list initially.  I probably wanted to copy and paste.  Still learning, I just feel dumb right now.  Thanks for looking. BTW with the Ubuntu drive and the new drive unhooked Windows loads normally.

Mark Shuman

---

