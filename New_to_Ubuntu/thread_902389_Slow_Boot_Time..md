---
title: "Slow Boot Time."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by diwas on 2008-08-27
My system specs are listed in my signature. I have compiz and emerald enabled. Addition to that i have an internet connection which has been designated to start during the boot time. 

But my boot time is damn slow. Too slow. Its abt 5 minutes or smthg. Is there anything which cud help me track which thing is taking time to load or execute?

I suspect compiz and emerald. Do they slow up the boot process???

Thank you

---

### Post by WRDN on 2008-08-27
If it takes that long, it sounds like it's hanging in places.
At bootup, select Ubuntu from the GRUB menu, and press "e". Now, select the kernel line and press "e" again. Remove the words "quiet splash" if you have not done so already. Now, press "b" to boot, and you will be able to identify where the boot is hanging.
You can make this change permanent by editing the GRUB menu file. Open the Terminal and type:

```
sudo gedit /boot/grub/menu.lst
```

Now, find the kernel line for the Ubuntu entry you boot, and remove the words "quiet splash". Finally, save the file.

---

### Post by Elfy on 2008-08-27
If you suspect compiz and emerald, did your startup time get slower once you'd enabled them.

You can also install bootchart and then you could post a scrnsht if you're not usre what is taking the boot time.

---

### Post by diwas on 2008-08-27
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
default		6

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
# kopt=root=UUID=846c49a4-0477-4476-9a92-fd7af457a4ce ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,8)

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
# defoptions=quiet splash vga=773

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
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=846c49a4-0477-4476-9a92-fd7af457a4ce ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=846c49a4-0477-4476-9a92-fd7af457a4ce ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=846c49a4-0477-4476-9a92-fd7af457a4ce ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=846c49a4-0477-4476-9a92-fd7af457a4ce ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,8)
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

```

Where is the line?

---

### Post by diwas on 2008-08-27
Oh yeah I have a cairo dock too, which loads up in start up....

EDIT: Also Icon theme...and metacity theme too.

---

### Post by Elfy on 2008-08-27
> title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=846c49a4-0477-4476-9a92-fd7af457a4ce ro [COLOR="Red"]quiet splash [/COLOR]vga=773
initrd		/boot/initrd.img-2.6.24-19-generic
quietHave a piece for paper handy for when it boots although if it takes 5 minutes I guess you could write a small story :)

---

### Post by nkri on 2008-08-27
Try [_this_]("http://ubuntuforums.org/showthread.php?t=254263") howto.  It took about 11 seconds off my boot time but it was only 50 seconds to begin with.  It works best on a system where the startup programs have changed a lot and since the files aren't in a completely logical order, it takes longer to boot.  BTW, the second tip doesn't work with Hardy (or Gutsy, as far as I know) because they made that the default:)

Also, make sure the programs you have running at startup are needed and necessary (for example, Tracker and the Tracker applet aren't totally needed...you can just go to Places>Search For Files to search for and find stuff faster with more advanced options).  I took a second or two off of my boot time by doing this as well:).

Good luck!
-nkri

---

### Post by collegeKid28 on 2008-08-28
What are "compiz" and "emerald"?

Thanks

---

### Post by Elfy on 2008-08-28
Compiz is a compositing windows manager - deals with all the - that looks good stuff, emerald is a window decorator.

[http://swik.net/emerald](http://swik.net/emerald)
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by Crafty Kisses on 2008-08-28
You could technically boot into verbose mode and see where it hangs.

---

### Post by diwas on 2008-08-29
I did the 1st tip (deleting stuff), and i saw it hung where it said smthg like : NTP server bla bla....and then it stopped "hanging" on Stopping NTP server.

But what xactly i came to know is that...after the GNOME DISPLAY MANAGER starts...it takes too long time. I have automatic login so that i dont have to type my name each time i open ubuntu. But still it takes like 1-2 minutes...
I changed the graphics effects to "normal" through "appearances". But still the same thing prevails.

Any solution?

---

