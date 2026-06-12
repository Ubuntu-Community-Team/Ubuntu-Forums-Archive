---
title: "Complete noob"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by Ride4zen on 2012-07-21
Ok...Have a Asus 1005 PEB netbook that has died since a Windows Update. Screwed the pooch and can't go to a workable restore point. Was advised to download Ubuntu to a USB drive and boot from there. Have downloaded, changed bios boot priority to usb, but nothing happens. WTF?
 
Asus uses Atom processor and Window 7 starter, does that have any effect? followed the step by step (such that it is) on Ubuntu website but still nothing.
 
Thanks in advance for help

---

### Post by popper668 on 2012-07-21
you could burn it to a dvd-disk and try that route or when you fire it up hit F12  and then choose usb?

---

### Post by NikTh on 2012-07-21
> **Ride4zen said:**
> Ok...Have a Asus 1005 PEB netbook that has died since a Windows Update. Screwed the pooch and can't go to a workable restore point. Was advised to download Ubuntu to a USB drive and boot from there. Have downloaded, changed bios boot priority to usb, but nothing happens. WTF?
 
Asus uses Atom processor and Window 7 starter, does that have any effect? followed the step by step (such that it is) on Ubuntu website but still nothing.
 
Thanks in advance for help
Hi ,

How you burned the .iso image to Usb ? 
Try again , 
download iso  from [_**HERE**_]("http://nl.releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.iso")
and use [_**Unetbootin**_]("http://unetbootin.sourceforge.net/") program to burn the .iso to Usb. 

Thanks

---

### Post by anewguy on 2012-07-21
+1 - to build an "ubuntu usb", or to make a livecd, you can't just copy the image to the media.  You won't end up with anything usable.  You have to "burn" the ISO image to the media (flash drive or cd).  For the flash drive you would use unetbootin as mentioned.  For the live cd you have to use a cd burning tool and select the "burn image" option.

---

### Post by Ride4zen on 2012-07-21
Ok. Did as instructed and nothing different happens. It contiunes to try and boot to Windows. Changed in priority in Bios and a Windows repair cd is bootable. ???

---

### Post by Daveth on 2012-07-21
you might try an alternative usb stick, as some do not play nicely booting up the .iso

---

### Post by techvish81 on 2012-07-21
sometimes USB boot is disabled in the bios, even if you change the boot order,  you have to enable it from bios.

---

### Post by westcoast01 on 2012-07-21
> **techvish81 said:**
> sometimes USB boot is disabled in the bios, even if you change the boot order,  you have to enable it from bios.
This is what I have to do on all three of my Asus, and after you install don't forget to change the boot order and reenable the hdd to boot from the hdd. Also on my Asus machines I have to F6 and select NOMODESET otherwise all I get is a black screen with a blinking dash on the upper left corner of the screen.  Let us know how things go, best of luck. : side note, I would strongly recommend adding another gb of ram. Two gb will make all the difference in the world.

---

### Post by Ride4zen on 2012-07-21
Thanks to everyone so far. 
 
Ok, decided to burn the image to an actual CD and try that...nada, same as USB. Boot order is correct but it goes directly to selection scene for Safe Mode or Normal Windows load. The times it accesses the CD it begins "Windows Setup" and get to a auto shutdown screen. The code call out as apparently been corrected on other machines by resetting CMOS battery.....
 
What's strange is this all started because when a 12 part Windows update downloaded, the machine would not boot.
 
Was advised Ubuntu would give me chance to see if maybe HD was AFU as suggested by a Geek Squad guy (another Geek Squad guy sez that the updates tell him it's not a HD but Windows issue and he suggested the Ubuntu fix)
 
I'm perplexed and about ready to just buy another machine.
 Too bad, I really like this thing.

---

### Post by NikTh on 2012-07-21
Hi , 
do not abandon the effort. 

Try something else.. go to bios configuration and disable everything except usb boot. 
I mean if you have this option : make usb the only boot device . 
An other option might be a single boot key. My MB has this option (F12) and i can boot to a single device without change anything in config bios page.

Regards

---

