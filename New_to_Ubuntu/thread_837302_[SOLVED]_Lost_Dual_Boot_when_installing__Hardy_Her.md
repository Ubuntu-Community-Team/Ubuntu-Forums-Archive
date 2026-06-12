---
title: "[SOLVED] Lost Dual Boot when installing  Hardy Heron"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by guhanr on 2008-06-22
Hi, 
Complete Newbie to Ubuntu - used to live on XP Home Edition. Had been flirting along the sidelines with a Hardy Heron LiveCD from a friend and finally decided to install. 

During install, the only options for partitioning I got were Use Full Disk (160GB), so I skipped that and picked the manual option. I had a D: drive, that I had already created (37GB) when I used to dual boot with Vista, which I removed long ago. So, I selected that drive, or so I thought and asked Ubuntu to use it. It warned me about a swap drive, so I created one for 3GB. All went well, and after installation, **I cant see a dual boot option**, that I had when before when running ubuntu from the CD drive. 

I read the forum posts 
[INDENT][LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=836446&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=836446&highlight=dual+boot)
[*][http://ubuntuforums.org/archive/index.php/t-1659.html](http://ubuntuforums.org/archive/index.php/t-1659.html)
[/LIST][/INDENT]

and was going to try and modify accordingly. However, I wanted to make sure I didnt end up doing any more damage, than I already did and wanted to seek advice. [-o<

I read the posts and frm what I understood, have posted the output from the commands below. 

> Output from cat /boot/grub/menu.lst

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
# kopt=root=UUID=424db901-b33b-41e0-aa2e-61f348545617 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=424db901-b33b-41e0-aa2e-61f348545617 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=424db901-b33b-41e0-aa2e-61f348545617 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

> cat /boot/grub/default results in a default file, that looks like this

```
default
#
#
#
#
#
#
#
#
#
#
# WARNING: If you want to edit this file directly, do not remove any line
# from this file, including this warning. Using `grub-set-default\' is
# strongly recommended.

```

> sudo fdisk -l  results in something weird like this : > sudo: timestamp too far in the future: Jun 22 23:32:09 2008 :confused:

I can see a 116.2 GB drive, which I mounted, and I can see the files on my Windows - That kind of tells me that all is not lost...:(. 

Can you suggest what I can do, to get the dual boot back?:-k

PS : I am sorry if this has been solved before and I didn't find it in the forums, but I wanted to make my situation clear, so that I didn't end up doing more damage...

---

### Post by guhanr on 2008-06-22
Updates:

Managed to find out why > sudo fdisk -l was acting funny. I bungled something on the time setting. Fixed it now and can see this

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131   de  Dell Utility
/dev/sda2               6       14180   113860687+   7  HPFS/NTFS
/dev/sda3           14181       19028    38941560    5  Extended
/dev/sda4           19029       19429     3221032+  82  Linux swap / Solaris
/dev/sda5           14181       19028    38941528+  83  Linux

```

Could someone please help with the changes I need to make to get my dual boot back?

many thanks..

---

### Post by Oldsoldier2003 on 2008-06-22
> **guhanr said:**
> Updates:

Managed to find out why  was acting funny. I bungled something on the time setting. Fixed it now and can see this

```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           5       40131   de  Dell Utility
/dev/sda2               6       14180   113860687+   7  HPFS/NTFS
/dev/sda3           14181       19028    38941560    5  Extended
/dev/sda4           19029       19429     3221032+  82  Linux swap / Solaris
/dev/sda5           14181       19028    38941528+  83  Linux

```

Could someone please help with the changes I need to make to get my dual boot back?

many thanks..
from a live cd this is what i would try
```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

This will install grub on the MBR and point it to your Ubuntu partition. If this fails you might need to hide your recovery partition from grub.

---

### Post by guhanr on 2008-06-23
> **Oldsoldier2003 said:**
> from a live cd this is what i would try
```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

This will install grub on the MBR and point it to your Ubuntu partition. If this fails you might need to hide your recovery partition from grub.

Thank you for responding - would like to make sure I understood correctly. You suggest that I **boot using LiveCD instead of the normal boot**. And after it boots from LiveCD, o**n a terminal window, type the code you suggested**? 

Pl let me know and I will try accordingly.

---

### Post by meierfra. on 2008-06-23
"fdisk" and "menu.lst" look fine. 

But I'm not quite sure what you current situation is:

Does the grub menu appears at boot up?
Are  you are able to boot into Ubuntu?
What kind of error message do you get when trying to boot XP?
Do you have the file "ntldr" on the XP partition? (It should be in the folder which opens if you double click on the icon for XP in Places->Computer)
You said you deleted Vista a long time again. But what was on the Ubuntu partition just before you installed Ubuntu?

---

### Post by guhanr on 2008-06-23
> Does the grub menu appears at boot up?

It didnt show up the first time I started. Yes, it does now, after I added this in menu.lst. 

```
title Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1
``` 

And then when I selected it, nothing happened. So, I turned the comp off and on, and I selected the Ubuntu option to get in. 

I dont know if the above code is right - I wrote it when my sudo fdisk -l wasnt working. Now that it is - is it still right?

> Are you are able to boot into Ubuntu?
Yes - thats where I am writing this from.

> What kind of error message do you get when trying to boot XP?
No error message, but nothing happens either. It just says "Starting Up...."

> Do you have the file "ntldr" on the XP partition? (It should be in the folder which opens if you double click on the icon for XP in Places->Computer)
I dont see a file called ntldr there...

> You said you deleted Vista a long time again. But what was on the Ubuntu partition just before you installed Ubuntu?


The files from the Vista Installation, but they werent doing anything - as in, I couldnt boot into Vista anymore after I removed. But I never did get around to deleting the files...

---

### Post by Duck2006 on 2008-06-23
Change this,

title Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1

to this,

title Windows XP Home Edition
root (hd0,1)
makeactive
chainloader +1

No savedefault.

---

### Post by sydbat on 2008-06-23
In your original post, in the GRUB menu list, at the very bottom it says "Windows Vista/Longhorn (loader)"...I wonder if this is the problem...Windows looking for a loader that no longer exists? Might have to boot from the Windows XP disk to fix the Windows bootloader?

---

### Post by guhanr on 2008-06-23
> **Duck2006 said:**
> Change this,

title Windows XP Home Edition
root (hd0,0)
makeactive
chainloader +1

to this,

title Windows XP Home Edition
root (hd0,1)
makeactive
chainloader +1

No savedefault.
Phew! That seemed to fix it. Muchas gracias. I just realized that when I was playing with the LiveCD, I had setup somethign to ask re a dual boot and when I installed Ubuntu fully, I forgot all about it. 

So, when I boot up, I get about 6 options (XP Home, Ubunutu generic, recovery...,Longhorn). When I pick XP Home, it asks me again for XP Home or Ubuntu. I picked XP and all is well! The second Ubuntu I think it is set to run from CD - but I was too chicken to try..:)

Anyways, thanks again. 

PS- Now that I know XP works, will xperiment with 8.04 more (not grub tho :P) and hopefully will convert, fully! :)

---

### Post by meierfra. on 2008-06-23
Glad you got it to  work.

(Sorry, I assumed you had tried the Vista entry on the Grub Menu. That boots up XP as well. So  I was looking for more complicated solutions)

The second Ubuntu does not boot the CD, but it boots you into recovery mode.

---

### Post by guhanr on 2008-06-23
> Glad you got it to  work.
Happy as a kid who has tied his laces by himself, for the first time! :) <grin>

> (Sorry, I assumed you had tried the Vista entry on the Grub Menu. That boots up XP as well. So  I was looking for more complicated solutions)
Thank you so much, for pointing me, anyways. 

> The second Ubuntu does not boot the CD, but it boots you into recovery mode.

As I found out this morning - the default option is XP and when that gets selected, and I pick Ubuntu from the second option that comes up.. I get a bash shell! Imagine my surprise(!) and then I MS-ed my way (hard reboot) and then I see your post :) People like me, hit all the walls in a maze, before getting out! :)

PS _ Any idea how I can get rid of so many options that show up (generic, recovery, dell, vista and so on..) to show just XP Home or Ubuntu? Tks...

---

### Post by guhanr on 2008-06-23
Just marking the thread solved. Didnt realize the forum had a tool for it.. tried changing subject.. and ended up creating a re-post. Oops!

---

### Post by meierfra. on 2008-06-23
> then I MS-ed my way (hard reboot) and 

Type "reboot"  or "shutdown now"  to get out of recovery mode.


> Any idea how I can get rid of so many options that show up (generic, recovery, dell, vista and so on..) to show just XP Home or Ubuntu? 

 
To  get rid of Dell and Visa, just delete this
 
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

from menu.lst.    I recommend leaving  the Ubuntu recovery mode on menu.lst. It might  come in handy sometime in the future.

> 
the default option is XP 


Where did you put  the Windows Item?  It needs to be either just above the line

### BEGIN AUTOMAGIC KERNELS LIST


or below the line

### END DEBIAN AUTOMAGIC KERNELS LIST


Otherwise, your Windows item will disappear after the next kernel update.
Talking about kernel updates: Click on drs305 in my signature, to learn how to keep you Grub Menu neat and tidy during kernel updates.

---

### Post by guhanr on 2008-06-23
> Type "reboot"  or "shutdown now"  to get out of recovery mode.
Will try the next time

> To  get rid of Dell and Visa, just delete this ... from menu.lst.    I recommend leaving  the Ubuntu recovery mode on menu.lst. It might  come in handy sometime in the future.

Didnt delete- commented it out(#), which I guess will have the same effect?. Will try a reboot shortly and update the thread

> Where did you put  the Windows Item?  It needs to be either just above the line

### BEGIN AUTOMAGIC KERNELS LIST

or below the line

### END DEBIAN AUTOMAGIC KERNELS LIST


Otherwise, your Windows item will disappear after the next kernel update.


I have now placed the Windows Item before the ### BEGIN AUTOMAGIC KERNELS LIST


> 
....
....
# Based on instructions from [http://ubuntuforums.org/showthread.php?t=837302&page=2](http://ubuntuforums.org/showthread.php?t=837302&page=2). 
# Guhan: begin customization code #

title Windows XP Home Edition
root (hd0,1)
makeactive
chainloader +1
no savedefault

# Guhan: End customization code ###

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
....
....



>  Talking about kernel updates: Click on drs305 in my signature, to learn how to keep you Grub Menu neat and tidy during kernel updates.
Will do.

---

