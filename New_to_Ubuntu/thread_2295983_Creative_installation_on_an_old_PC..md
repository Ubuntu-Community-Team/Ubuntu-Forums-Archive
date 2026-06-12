---
title: "Creative installation on an old PC."
date: 2015-09-22
forum: New to Ubuntu
---

### Post by fred63 on 2015-09-22
Greetings. I am about to get started and I have a few questions.

1. My PC is an old one - PIII 733 Mhz running Windows XP. 512 MB of RAM. I have about 4 GB of free space in an NTFS partition, a single partition on a 10 GB drive. My plan is to dual boot XP and Ubuntu so I can test out Ubuntu. If all goes well I will blow the whole thing away and set up a dedicated Ubuntu install

3. My PC has only a cd-writeable drive, it has no DVD which makes installing the newest version of Ubuntu problematic at best, my research tells me that current ISO images are too big for a CD_ROM. I see on this web page [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)  that numerous older versions are available. I request some advice on which version to download so that I can burn an iso image on to a CD-ROM.

I am hoping that the install CD I burn has a program that will resize my NTFS partition so I can set aside a partition for Ubuntu.
My question is: Can this all be done?  If so, is 4GB enough for a basic Ubuntu install?

I'll just add that although I am new to Linux, I am quite computer savvy. Cheers.

---

### Post by overdrank on 2015-09-22
Hi and welcome, you can try [_lubuntu 12.04_]("http://lubuntu.net/tags/lubuntu-1204") but I believe the minimum space is 4.3 gb.

---

### Post by yancek on 2015-09-22
> I am hoping that the install CD I burn has a program that will resize my  NTFS partition so I can set aside a partition for Ubuntu.

Ubuntu and most of its derivatives have GParted on the Live CD which is a graphical partition manager.

> is 4GB enough for a basic Ubuntu install?

No.

You can check out some Ubuntu derivatives such as Lubuntu or Peppermint or others.  Don't know if any of them will fie on a 4GB partition but will fit on a CD.  512MB is the minimum RAM for Ubuntu, some other derivatives might work.

---

### Post by grahammechanical on 2015-09-22
There are some rules for dual booting Windows and Linux. They come in no particular order

1) Defrag Windows using Windows utilities and do it more than once and restart Windows each time
2) Use Windows utilities to resize Windows partitions.
3) Have a Windows restore/recovery disk available
4) Back up your data.

There may be others as well. The amount of RAM limits your options and so will the graphic adapter and the amount of memory that it has. The CPU is 32 bit so you will need a 32 bit version of the OS (called i386). You best be thinking of the Lubuntu Alternative Install ISO image. I doubt if you have the RAM and video memory to run a Graphical User Interface installer.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

Regards.

---

### Post by SuperFreak on 2015-09-22
> **yancek said:**
> Ubuntu and most of its derivatives have GParted on the Live CD which is a graphical partition manager.

It would be prudent to use Windows software to change partition sizes of Windows (NTFS) partitions particularly the OS partition. It has been know when using GParted or Linux based partition tools to partition the Windows OS partition for Windows to no longer work

Edit: grahammechanical beat me to the post with a better answer

---

### Post by fred63 on 2015-09-22
Thanks for the tips people. My initial impression from the posts and some reading that I have done is that dual booting Ubuntu on this particular machine is not the best way to go. Maybe I'll take a look at some other flavor's of Linux that hopefully aren't as demanding resource wise. Mostly I will be needing this machine for some light web browsing and computer programming which is a hobby of mine, so my needs aren't really that great.

Cheers.

---

### Post by Geoffrey_Arndt on 2015-09-23
Fred63 . . . none of the buntus will be a satisfying experience (at the least) on that type of PC.    One possibility (of only a handful) would be antiX.    It will run pretty well on a 512 meg machine - - you can get the iso at distrowatch.com.

One of the lightest desktops is "Fluxbox" . . . which is an option in antiX.     (btw antiX is based on debian testing . . . which is also the "mother-ship" for ubuntu).   Fluxbox isn't the most aesthetic desktop (kinda butt ugly but it works).

[http://www.distrowatch.com](http://www.distrowatch.com)

IF wanting a really good Ubuntu experience - consider a used PC with 4 gb ram, an Intel core i3 or i5, and a decent hdd (160 gb or more).   All Intel works best re out of the box compatibility (Intel video and Intel Wireless) = plug & play.

---

### Post by mastablasta on 2015-09-23
Lubuntu or LXLE should work, but slow.

you can also install it to USB stick. they are cheap. though not as fast as hard disk.

as others said you can get a used laptop at a relatively low price. and you will have a lot better experience.

AntiX (debian/mepis based) is also a good option for older PC's. As are Ubutnu based ToriOS and Bodhi Linux.

---

### Post by Mike_Walsh on 2015-09-23
Hi, fred63. And welcome to the forums.

Grahammechanical's advice is sound, as regards preparation  of the disk prior to installing Linux. And I will agree with Geoffrey_Arndt as far as AntiX goes. However, I'm going to make another suggestion.....and others on the forums here must be getting fed up with me over this by now!

Have you considered trying 'Puppy' Linux? It's a very small. lightweight Linux distro that is also extremely versatile in its installation requirements. Yes, you **can** install it to a hard drive.....but Puppy's normal mode of operation is running from a USB flash drive. It will even run from floppies or Zip drives! Average Puppy size is between 150-220 MB; the entire thing sits in, and runs from, RAM.....so even 512 MB is quite satisfactory for operation at an acceptable speed. If you have USB ports on your old machine, you should be well set up for trying it. The obvious advantage of this is that you don't have to disturb your Win XP installation...as long as you have the ability to boot from USB.

Puppy has the advantage of 'persistence'; the ability to save your programs, settings & configuration files back to the same flash drive it's installed on; a development of the original 'persistence' mode pioneered by the German developers of [Knoppix]("https://en.wikipedia.org/wiki/Knoppix"). Ubuntu uses persistence, too.....but only from a 'live' USB, which is not really a permanent solution. However, it's a very much cheaper option than forking out for a new machine, or even parts to upgrade your existing one...

I know people on the Puppy Linux Forums who happily run Puppy from a Pentium II & 256 MB of RAM.

I myself use an elderly Dell Inspiron laptop.....an original 1100, from 2002. It came with a P4-gen Celeron when new, 128 MB of RAM, and a 20 GB HDD. It was supplied with Win XP.....which ran very slowly; 'steady' would be a more polite way of putting it! It now runs a 2.6 GHz PIV, has the maximum of 1 GB of RAM, and a 40 GB HDD. It was one of Dell's very first machines with the then-new USB 2.0 ports.....and the ability to **boot** from USB. She runs three 'Pups' from the hard drive (in addition to Xubuntu), and a further two from flashdrives.

I would recommend giving 'Puppy' a try; if you would like to, ask on the Puppy Forums:-

[http://www.murga-linux.com/puppy/index.php](http://www.murga-linux.com/puppy/index.php)

The Forum members will make you very welcome, and would be more than happy to help you select a suitable distro to run on your machine; at last count, there were somewhere in the region of over 400 variations & re-spins...and many of them are based on recent Ubuntu distributions, so you would have access to the Ubuntu repositories. I would thoroughly recommend it for older hardware.

Hope that helps. You'll find me there, under the same name.


Regards,

Mike. ;)

---

