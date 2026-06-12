---
title: "Installing Hardy without CD, Network or USB?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Angus77 on 2008-05-07
Hi, I've got an old 500MHz desktop that has Gutsy running on one partition right now, and I'd like to install Hardy as well.

There are a few problems:
   1)  The CDROM is a bit wonky lately, so a CD install is not possible
   2)  It's the computer I use at work, and the company won't let me connect to the network
   3)  The BIOS is so old that it won't boot from USB

It does have a 3.5" floppy drive, though! :p

So I was wondering if it was possible to install Hardy on an empty partition from another partition I was using (I've got Gutsy on one partition, and XP on another (although I haven't used that partition in almost a year!)).

---

### Post by nick09 on 2008-05-07
Try installing a replacement CD-rom player.

---

### Post by Delever on 2008-05-07
You still have to find a way to get it in computer! Like, temporary replacing CD rom.

---

### Post by Joeb454 on 2008-05-07
Erm, wow...I don't really know how else you can actually install a distro.

You could try doing a minimal install of Ubuntu and building it up from there if you're feeling a little adventurous - there's a wiki page for this too :) I'll try and find it.

Edit: Found it :)

[Minimal Install Wiki Page]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by Delever on 2008-05-07
> **Joeb454 said:**
> Erm, wow...I don't really know how else you can actually install a distro.

You could try doing a minimal install of Ubuntu and building it up from there if you're feeling a little adventurous - there's a wiki page for this too :) I'll try and find it

Still... getting that "minimal" amount using floppy drives... *shivers*.

---

### Post by MDSmith2 on 2008-05-07
I don't think ubuntu has anything small enough for a floppy but debian has a floppy sized iso that downloads the system without a cd. [http://www.debian.org/distrib/netinst#verysmall](http://www.debian.org/distrib/netinst#verysmall)

---

### Post by oilchangeguy on 2008-05-07
does the computer meet these requirements?
System Requirements 
Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least 4 GB of disk space.

what are you hoping to do with a 500mhz cpu computer? it won't be able to do all of the things 8.04 is able to do.

---

### Post by lazyart on 2008-05-07
Dude, you're trying to start a car without keys, gas or a motor.

Stop being silly and get a CDROM or just stick with Gutsy.

---

### Post by Angus77 on 2008-05-08
What I was hoping was that maybe I could install it to an empty partition while actually running Gutsy...?  Or is that just not doable?

I can use USB while the system's on, so I can plug in an external drive and transfer the .iso to the internal HD.  I just can't boot from USB (no option in the BIOS).

Gutsy runs fine on the system, so I don't _need_ to put on Hardy.  I just _want_ to, you know? (so I can have the same OS at work as at home)  (while being too cheap to buy a CDROM for it.  I don't want to throw any money at a system that I'm probably going to throw out in the next year or two)

---

### Post by Archmage on 2008-05-08
You can mount the alternate CD-ISO, and than install it.

I would suggest to get the ISO on your PC via an extern harddrive on USB. Spliting the ISO on floppy discs and than copy them on the PC would take ages (700 MB fit on 500 floppy discs).

---

### Post by hyper_ch on 2008-05-08
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by louieb on 2008-05-08
Hum you have a floppy drive and you can  put the iso on the hard drive. 
Seems this guy has figured it out.
[HOWTO: Install Edgy 6.10 from an .iso file - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=316093")

Should work for Hardy too.

---

### Post by hyper_ch on 2008-05-08
no need for floppies... you can install it directly from your harddisk... see the above link.

---

### Post by talsemgeest on 2008-05-08
Another idea is pulling out the harddrive, sticking it in another computer to install hardy, then putting it back in. Some of the hardware might not be recognized properly, but it might be worth a shot...

---

### Post by Angus77 on 2008-05-08
```
https://help.ubuntu.com/community/In...tion/FromLinux
```

I think this is what I was looking for!  If I have the time, I'm gonna try it tomorrow.  Thanks!

---

### Post by gn2 on 2008-05-08
Maybe give Xubuntu a try, it should run better on that PC.

---

### Post by Angus77 on 2008-05-09
It worked nicely! Oh, beautiful day!

@ gn2:

I originally did install xubuntu.  Then I ended up trying Gnome on that installation and it worked fine, so that's what I've bee using ever since.  

The lesson is:  Have faith!

---

### Post by hyper_ch on 2008-05-09
> **Angus77 said:**
> It worked nicely! Oh, beautiful day!

good to know.. I've never tried to install it from the harddisk myself *g*

---

### Post by aeiah on 2008-05-09
just out of curiosity, what kind of company makes you use a 500mhz computer, and also doesnt let you attatch it to their network?

---

### Post by gn2 on 2008-05-09
Superb, you can surf to the radar station on it now, the mascara snake gets there faster with Xubuntu, Gnome is too fat and bulbous..... :D

---

### Post by Angus77 on 2008-05-10
@ aeiah

They don't make me.  They don't provide me with a computer at all--when I took the job, I was expected to write up all documents & faxes by hand (this is Japan.  They fax like crazy here).  I didn't like that, so I brought in my father-in-law's computer when he was about to throw it out.

There's a Windows box in the office now, but it's shared by half a dozen people, and none of us have the administrative rights to add software, etc.  Windows & MSOffice drive me up the wall, so I only use the thing to send emails and to print off things I've typed up on my Ubuntu box (I have my own printer, but the company has a nice laser printer, so...)

I'm not allowed to attach it to the network because it's not a company computer.

@ gn2

What on God's Golfball on you going on about? ;)

---

### Post by Angus77 on 2008-05-10
I hope they bring back the "Mark Thread As Solved" option...

---

### Post by gn2 on 2008-05-10
> **Angus77 said:**
> 
@ gn2

What on God's Golfball on you going on about? ;)

You're not familiar with the works of the man in your avatar? Shame on you!

[http://www.beefheart.com/index.html](http://www.beefheart.com/index.html)

[http://www.shiningsilence.com/hpr/lyrics/pena.php](http://www.shiningsilence.com/hpr/lyrics/pena.php)

Fat and bulbous was my play on words for fast and bulbous.....
Xfce = fast 
Gnome = fat

---

### Post by jeffus_il on 2008-05-10
> **aeiah said:**
> just out of curiosity, what kind of company makes you use a 500mhz computer, and also doesnt let you attatch it to their network?
Maybe he keeps bad [COLOR=Red]company[/COLOR]!:)

By the way, in this sorry situation, I would copy the alternate CD to a USB Stick and run the install script to install, (He can't boot usb, but I assume, can read it)

---

### Post by Angus77 on 2008-05-10
@ gn2

> "Earth...god's golf ball."

Here's a [page of quotes]("http://members.aol.com/tedalvy/cbq.htm") you might be interested in.:guitar:

---

