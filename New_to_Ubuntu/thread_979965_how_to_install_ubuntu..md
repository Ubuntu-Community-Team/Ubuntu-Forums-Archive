---
title: "how to install ubuntu."
date: 2008-11-12
forum: New to Ubuntu
---

### Post by sjaakske on 2008-11-12
hello,

I have an pretty old pc, and want to install ubuntu on it.
But i have some problems doing that.
There is already windows xp on it, and hope to get sort of a dualboot pc, so i can use both.
The problems are that the pc won't boot from a disc.
and i don't have internet on that pc.
I already tried to update the Bios, so i could boot from the disc. But the floppy drive didn't work at all.
And I tried to install from a usb drive, but then i need internet to install.

so is there a ubuntu version for usb, that u can install, without internet, floppy's and disc's?

well i am a total noob to this, so hope someone can help :).

[SIZE="2"]sorry for my bad english[/SIZE]

---

### Post by Idefix82 on 2008-11-12
The first google result when you enter ubuntu install usb:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by sjaakske on 2008-11-12
read the whole thing, but i think i would need, to boot from the usb then. And since my pc will only boot from the hard drive, I guess that won't work.
thanks for the fast reply anyways.

hope someone else knows a way to boot from my harddrive. without network, cd and floppy.

---

### Post by youthforlinux on 2008-11-12
how about download the desktop iso to a usb disk from another computer download wubi and put that .iso file in the same folder and wubi will use that disc to do it, thats an easy solution....

---

### Post by cariboo on 2008-11-12
If your CDrom drives works at all, you can do a wubi installation, It instll Ubuntu inside windows. Just insert the cd and a menu will come up with different options. If you have the LiveCD on usb you should see the same options.

JIm

---

### Post by sjaakske on 2008-11-12
i tried to install wubi, but when i do that when i am at like 40% it says, make now connection to internet. if i click cancel, the setup quit's.
and it still ain't installed

---

### Post by Keen101 on 2008-11-12
Installation from a USB drive should not need internet.  It might ask for it, but it should not need it.

Can i ask how you got it on the usb?

These two methods should work for getting it on a usb.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

......................

the only other method i can think of is put the hard drive in another computer with a cdrom drive.

.......................

ubuntu is actually pretty dependent on internet. It's not needed, but if you want to install extra programs you will have to download .deb files or .run files, or compile source code.

---

### Post by youthforlinux on 2008-11-12
there's no point putting it onto a usb disk if it cannot boot from it except using it for wubi....

---

### Post by zakirs on 2008-11-12
well why did u press cancel .. leave that wubi gives u install even if u leave it unattended

---

### Post by Kevbert on 2008-11-12
Have a look at this [[COLOR="Red"]website[/COLOR]]("http://www.pendrivelinux.com/"), it may help. In many cases you need a CD with the operating system on it.

---

### Post by sjaakske on 2008-11-12
> **Keen101 said:**
> Installation from a USB drive should not need internet.  It might ask for it, but it should not need it.

Can i ask how you got it on the usb?

These two methods should work for getting it on a usb.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

[https://launchpad.net/liveusb](https://launchpad.net/liveusb)

......................

the only other method i can think of is put the hard drive in another computer with a cdrom drive.

.


if i use those programs would it just like that wubi file, that just save ubuntu to the harddrive. or more like that bootable cd, so that i have to restart the pc, and install it like windows xp or something?

and i can't put the hard drive in this pc, cause it only has 1 IDE plug :(

**Edit:** wow thanks everybody for those fast replies :)

---

### Post by sjaakske on 2008-11-12
> **Kevbert said:**
> Have a look at this [[COLOR="Red"]website[/COLOR]]("http://www.pendrivelinux.com/"), it may help. In many cases you need a CD with the operating system on it.

the pc wont boot from flash

Edit
@ zakirs, it won't continue, if i let it stay at that window. i also can click on again,(dont know what would stay there if it was in english) but well i just dont have a network the

and sorry for the dubbelpost :(

---

### Post by Kevbert on 2008-11-13
Have you seen [[COLOR="Red"]this[/COLOR]]("https://help.ubuntu.com/community/Installation/FromWindows")?
What are your PC specs ? RAM memory, free hard disk size?

---

### Post by Paqman on 2008-11-13
> **sjaakske said:**
> i tried to install wubi, but when i do that when i am at like 40% it says, make now connection to internet. if i click cancel, the setup quit's.
and it still ain't installed

It has to make a connection to the internet to download the files that it will use to install the system.

You can get Ubuntu to send you free CD that you can use to install without needing an internet connection.

---

### Post by bennachie on 2008-11-13
This discussion seems to be going round in circles. I assume that your computer will boot into Windows XP. If you then insert an Ubuntu LiveCD, you should be presented (through AutoPlay)with a dialogue offering you the opportunity to install Ubuntu within Windows (this actually means that Ubuntu will operate under Wubi, but there is no need separately to install Wubi). If you accept the offer, Wubi will source all the information it needs from the CD, with no need to access the Internet.

That will allow you to evaluate (and hopefully be impressed by) Ubuntu. However, without some access to the Internet, you won't experience the full range of opportunities that Ubuntu offers you (of course, the same is true in spades for XP). 

Note that the one thing that Ubuntu doesn't do all that well is handle dialup access, mainly because so many modems are Windows-dependent, but version 8.10 does work well with quite a range of broadband dongles if you can't get ADSL.

---

