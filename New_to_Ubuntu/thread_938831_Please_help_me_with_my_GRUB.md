---
title: "Please help me with my GRUB"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by bennmann on 2008-10-05
I have two Ubuntu installs, one on an 100gb externally enclosed IDE to USB that I made to play Spore (clean install + wine = fantastic) and my original Ubuntu on my internal SATA 500GB Maxtor. I don't want to do a clean install on the internal drive, as I'd have to spend several more hours reconfiguring my mangled and yet beautiful wine installations. 

When the external is unplugged, and I tell my BIOS to boot to the internal, the Grub returns error 21. Many searches and hours of looking around hasn't helped. My device.map on the internal is (hd0)	/dev/sda and below I'll post my menu.lst. Maybe someone will see something I have yet to read about.

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
# kopt=root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro

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
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e5ea9bb4-2c12-4fc7-b881-683d84358cd8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

I've also auto-detected my 500GB in the BIOS of my gigabyte p31 (not p35). And I can start the internal Ubuntu when the external Ubuntu is plugged in. It's grub is fine and dandy.

---

### Post by kansasnoob on 2008-10-05
With the external drive unplugged boot the live CD (run without changes to computer) and follow the steps here to restore grub to the internal drive:

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

---

### Post by bennmann on 2008-10-05
You are a scholar and a gentleman. Solved. 

Anyone who has this problem please note that you have to follow the directions exactly to fix the grub. I first booted to the 500GB maxtor and tried from there before doing it with a livecd; only the LiveCD works.

---

### Post by andre_orwell on 2008-10-07
Hi,

I have a similar problem... and would really appreciate some advice on a fix.

I have a windows (XP Home) laptop and have installed ubuntu 8.04 (in the process of upgrading to 8.10 as I write) on an external USB drive.  It all works fine except that I have to have the USB drive plugged in for the system to boot.

I had hoped that the ubuntu install would leave the internal drive untouched so that I could just specify which drive to boot from via the bios (which is easy on this particular lappy).  But I have grub on the internal drive.

From what I have read I think the following is the correct solution:
1. install grub on the USB drive
2. run fixmbr on the internal drive

I really don't want to break things so can anyone confirm, deny or otherwise advise?

Thanks in advance.

---

### Post by caljohnsmith on 2008-10-07
> **andre_orwell said:**
> Hi,

I have a similar problem... and would really appreciate some advice on a fix.

I have a windows (XP Home) laptop and have installed ubuntu 8.04 (in the process of upgrading to 8.10 as I write) on an external USB drive.  It all works fine except that I have to have the USB drive plugged in for the system to boot.

I had hoped that the ubuntu install would leave the internal drive untouched so that I could just specify which drive to boot from via the bios (which is easy on this particular lappy).  But I have grub on the internal drive.

From what I have read I think the following is the correct solution:
[COLOR="Blue"]1. install grub on the USB drive
2. run fixmbr on the internal drive[/COLOR]

I really don't want to break things so can anyone confirm, deny or otherwise advise?

Thanks in advance.
You got it exactly right. :) Just make sure your BIOS supports booting from your USB drive, otherwise putting Grub in its MBR (Master Boot Record) won't help boot that drive. If you run into any problems, let us know.

---

### Post by dereferenced on 2008-10-07
Hi
I just installed windows xp. I thought naturally it would wipe off grub. But it did not and I could see only windows xp on the list. so I rebooted on live cd and setup grub on (hd0,5). Now I dont see xp on the booting list. Actually the list just doesnt come up. Ubuntu is booting up without giving any options.

I updated my menu.lst file to accomodate windows by adding following lines,

title Microsoft Windows XP Professional
root (hd0,0)
#savedefault
makeactive
chainloader +1

I tried with (hd0,1) too. But windows xp is just not showing up in the list, actually the list itself is not at all coming up while booting.

Please help. Thanks in advance. :)

---

### Post by caljohnsmith on 2008-10-07
Dereferenced, probably in your menu.lst you have "hiddenmenu" uncommented, so if that is the case you should change it to:
```
#hiddenmenu
```
If that doesn't solve your problem, then post the output of:
```
sudo fdisk -lu
```
And we can go from there.

---

### Post by dereferenced on 2008-10-07
That was awesome caljohnsmith! Thank you :D

---

### Post by andre_orwell on 2008-10-07
> **caljohnsmith said:**
> You got it exactly right. :) Just make sure your BIOS supports booting from your USB drive, otherwise putting Grub in its MBR (Master Boot Record) won't help boot that drive. If you run into any problems, let us know.

Fantastic... so I have the right idea.  As for the fine details, can you confirm the following is sufficient:

Install grub means specifically:

 - open a terminal and run:
     sudo grub-install hd1

(NB hd1 is correct for my system, but 
 should it be '(hd1,0)'? or is it better to use /dev/hdb1 etc
 should I also  use --root-directory=/boot)

After just this step will I be able to boot both ways (from the internal HDD and by telling the bios to boot the from the USB drive?)  Just curious for testing...

I find it is remarkably difficult to find definitive and easy to follow information on grub.  The manual pages are pretty terse.

---

### Post by caljohnsmith on 2008-10-08
> **andre_orwell said:**
> Fantastic... so I have the right idea.  As for the fine details, can you confirm the following is sufficient:

Install grub means specifically:

 - open a terminal and run:
     sudo grub-install hd1

(NB hd1 is correct for my system, but 
 should it be '(hd1,0)'? or is it better to use /dev/hdb1 etc
 should I also  use --root-directory=/boot)

After just this step will I be able to boot both ways (from the internal HDD and by telling the bios to boot the from the USB drive?)  Just curious for testing...

I find it is remarkably difficult to find definitive and easy to follow information on grub.  The manual pages are pretty terse.
First of all, I totally understand your frustration in finding a good Grub guide; one of the best resources for learning Grub is actually not the Grub manual, but Herman's website:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Herman's website is great because is focuses on practical solutions and troubleshooting of Grub problems, so it's not just some dry manual documenting all the features of Grub.

About that "grub-install" command that you refer to, it is not necessary to use that command unless Grub has never been installed before, i.e. the /boot/grub or /grub directory does not exist and have all the necessary Grub files. If you all ready have Grub installed like you do, it is better to use the Grub CLI to reinstall Grub to the MBR (Master Boot Record) in the following manner:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR of whichever drive Ubuntu is on. Then all you have to do is set your BIOS to boot the Ubuntu drive, and that should be all it takes to boot Ubuntu. If you want to boot Windows, the easiest is to just add a Windows entry in your Grub menu so you don't have to switch BIOS boot order every time you want to boot Windows. To add Windows to your Grub's menu, when you get into Ubuntu, open a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst

```
And at the bottom of that file add:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Most likely that will work (it is an educated guess on your setup), so if it doesn't work, you'll need to post:
```
sudo fdisk -lu
```
Let me know how it goes. :)

---

### Post by andre_orwell on 2008-10-08
[QUOTE=caljohnsmith;5928683]First of all, I totally understand your frustration in finding a good Grub guide; one of the best resources for learning Grub is actually not the Grub manual, but Herman's website:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)




Totally agree - a real gem!  It is hard to learn something like grub by experimenting.  It's great the way Herman explains exactly what is going on with each command.  The SuperGrubDisk also looks invaluable when combined with the instructions at [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

I also discovered the grub "wizard thing" which hides behind the advanced tab of the kubuntu system settings.  This is nice in so much as it finds the relevant drives and partitions for you and offers a little advice on the consequences of your selection... I remain reserved about putting a GUI on anything that can totally break your system however... mixed messages.

So, with gratitude, I can now report that I have grub installed on my removable drive and can boot directly from it :)

Thanks

---

### Post by andre_orwell on 2008-10-08
Things are very happy now!  I put a copy of the SuperGrubDisk distro on a USB stick and used that to fix the MBR of my internal drive to reboot windows directly.  Followed the simple instructions here [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)
Only 1 thing was confusing: after selecting "Fix Boot of Windows" you get another menu from which you must select "syslinux".  Not entirely intuitive!  So I didn't even need to pull out my old XP install disk :)

Anyway I now have what I wanted: and external drive with ubuntu that I can plug in and boot from... and when its *not plugged in* windows just boots as normal.

:guitar:

Thanks again.

---

### Post by caljohnsmith on 2008-10-08
That's great news, Andre, that you got the booting problems straightened out; glad I could help out. Cheers and have fun. :)

---

