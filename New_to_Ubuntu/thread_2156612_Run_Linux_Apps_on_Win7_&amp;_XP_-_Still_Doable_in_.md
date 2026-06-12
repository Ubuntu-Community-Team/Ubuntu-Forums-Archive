---
title: "Run Linux Apps on Win7 &amp; XP - Still Doable in Wubi, KDE/Win ???"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by GregA on 2013-06-22
Hello All, 

Am doing demo on certain Notes Pims, Tree databases and one in particular that's been requested . . . BasketNotes . . . a well implemented, super fast QT/KDE application.

How do I do this on a Win7 or XP box . . . in other words, ..... 

> > > Is Wubi still viable in Win 7 & XP?  Does Wubi require a dual-boot or can it be called up via a standard desktop icon??   

> > >  Is KDE intstallable on Windows without first installing Wubi?  If so, are programs installed/uninstalled via a package manager embedded in KDE like Apper or Muon???

Appreciate any info - thanks.

---

### Post by dino99 on 2013-06-22
wubi is dead
use virtualbox instead

---

### Post by GregA on 2013-06-22
I'm looking for the simplest, most reliable way to accomplish this.  Are the virtual machine systems about the same regarding setup and operation?  I'm not needing a tutorial here, but just the informed opinion of typical Ubuntu users that have actually implemented this solution (my audience has both system admins and casual users).

---

### Post by grahammechanical on 2013-06-22
Wubi has been found to be incompatible with Windows 8. Note the warning at the top of this page.

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Wubi allowed us to install Ubuntu inside Windows but it gave the impression of a dual boot. It was never intended to be a permanent solution but only as a trial period method to allow greater testing to decide if to install Ubuntu as a true dual boot.

So, the virtual machine route is to be preferred in your case and those of you clients. Ubuntu is installed into the virtual machine by directing the VM to run the Ubuntu live session DVD and install as normal. Applications are installed as normal - through the software centre or the terminal. The 13.04 software centre has an application called BasKet Note Pads. Is that the application that is being requested?

Developer web site.

[http://basket.kde.org/](http://basket.kde.org/)

KDE apps should run fine on standard Ubuntu but they are of course developed for the KDE environment so look at Kubuntu for you clients.

Regards.

---

### Post by newb85 on 2013-06-22
Please steer clear of Wubi.  If you want to stay in Windows and only run Ubuntu for that one program, you're probably best off running a virtual machine inside Windows.  (Wubi is *not* a virtual machine.  It's a dual-boot setup using the Windows bootloader and a virtual filesystem within your Windows partition.)  VirtualBox is probably the best VM software, but if you already have one you're familiar with and like, I would suggest you try that first.

---

### Post by GregA on 2013-06-24
Thanks . . . am going to install Virtual Box via Windows, then install both Ubuntu and Kubuntu.  Some users know about Ubuntu and want to see it & Unity, others just prefer the standard PC type of gui.

Regards,

Greg

---

### Post by monkeybrain2012 on 2013-06-24
Or you can install Ubuntu in an external hard drive or a flash drive.

[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

He wrote it for lubuntu10.04 but the key points are the same for newer versions of Ubuntu may be with some trivial modifications. Very Important: Pay attention that you install the bootloader in the flash drive instead of your internal hard drive.

I don't know how well does vbox support 3d accelerated desktops, but there seemed to be some issue with earlier versions so you may not be able to demo Unity in vbox.

---

### Post by dshgna on 2013-06-24
> **GregA said:**
> Hello All, 

Am doing demo on certain Notes Pims, Tree databases and one in particular that's been requested . . . BasketNotes . . . a well implemented, super fast QT/KDE application.

How do I do this on a Win7 or XP box . . . in other words, ..... 

> > > Is Wubi still viable in Win 7 & XP?  Does Wubi require a dual-boot or can it be called up via a standard desktop icon??   

**Wubi is viable with Win 7, nut no it cannot be run from a windows desktop. I agree with others that Virtualbox is a better alternative, but for me a live cd would be the best.**

> > >  Is KDE intstallable on Windows without first installing Wubi?  If so, are programs installed/uninstalled via a package manager embedded in KDE like Apper or Muon???

**No, KDE is based on the X Window System and not available on Windows. **

Appreciate any info - thanks.


**Hope this helps :)**

---

### Post by mastablasta on 2013-06-24
> **GregA said:**
> > > > Is KDE intstallable on Windows without first installing Wubi? If so, are programs installed/uninstalled via a package manager embedded in KDE like Apper or Muon???



have a look at [http://windows.kde.org/](http://windows.kde.org/)

yes there is a package manger for them and yes some KDE applicaitons can be installed in windows along with KDE. i have a number of them installed in windows.

wubi is not good for what you want to do.

to all others: let's not over complicate things...

---

### Post by kurt18947 on 2013-06-24
> **monkeybrain2012 said:**
> Or you can install Ubuntu in an external hard drive or a flash drive.

[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

He wrote it for lubuntu10.04 but the key points are the same for newer versions of Ubuntu may be with some trivial modifications. **Very Important: Pay attention that you install the bootloader in the flash drive instead of your internal hard drive.**

I don't know how well does vbox support 3d accelerated desktops, but there seemed to be some issue with earlier versions so you may not be able to demo Unity in vbox.


Oh yeah!  It's sort of a two step process when installing.  You have to choose the destination for the O.S. install - typically sdb if installing to a flash drive - _and_ a destination for the boot loader.  If you're new to Ubuntu's installer but are comfortable mucking about your machine's innards, you could unplug your hard drive.  Now there's no way you're going to overwrite anything on the hard drive.  You may have to change the boot order in your machine's BIOS, or there may be a key to press on boot to choose boot device.  Mine is F12 for instance.  I formatted a USB3 flash drive to ext2 and installed a 'real' (i.e. not a live USB) version.  Installing to a USB flash driver is slower than installing to a hard drive - writing to flash is a lot slower than reading - and updating is even slower.  But once the install is updated, it boots slower than from a hard drive but once booted it runs with reasonable speed IMO.

---

### Post by monkeybrain2012 on 2013-06-24
> **kurt18947 said:**
>   I formatted a USB3 flash drive to ext2 and installed a 'real' (i.e. not a live USB) version.  Installing to a USB flash driver is slower than installing to a hard drive - writing to flash is a lot slower than reading - and updating is even slower.  But once the install is updated, it boots slower than from a hard drive but once booted it runs with reasonable speed IMO.

Why ext2? I made a few to give to friends and I always format them as ext4. Yeah, flash drive is slower, but usable providing that you don't try to do 100 updates. :)  if you have an old hard drive lying around (say ripped from a dead laptop) you can install into it instead with the same method and you will get the same performance as you would installing into internal hard drive. Oh, and you would need to get a connection cable. :)

---

### Post by squakie on 2013-06-24
To answer another part of your question - if you start a virtual machine it will be just a click on an icon on the desktop.  if you are doing a presentation, start the vm before you start, minimize it, and then just click to open it in your presentation and you won't have to wait for system start up.   remember that if you are to use a projector to test it all out first.

i personally use virtualbox - it's free.  ater you install it, it's a simple matter of selecting new and just loading in ubuntu from either the iso image itself or from a dvd.  lots of help here to get you all set up.

---

### Post by kurt18947 on 2013-06-24
> **monkeybrain2012 said:**
> Why ext2? I made a few to give to friends and I always format them as ext4. Yeah, flash drive is slower, but usable providing that you don't try to do 100 updates. :)  if you have an old hard drive lying around (say ripped from a dead laptop) you can install into it instead with the same method and you will get the same performance as you would installing into internal hard drive. Oh, and you would need to get a connection cable. :)

I chose ext2 because it isn't journaled and so thought there'd be fewer writes and less wear in the drive.  I think it's possible for make ext4 non-journaling but I don't know how to do that and never took the time to research it.  Would ext4 with journaling disabled help with the speed, particularly the write speed?  I know it's recommended when installing SSDs  to make some changes in fstab.  I don't know if the same is true with USB flash drives or not.

---

### Post by monkeybrain2012 on 2013-06-24
I don't know about disabling journaling, but these flash drives are still alive and working after many rewritings over three years, for something you get for $10 it is more than worthy already. :)

---

### Post by kurt18947 on 2013-06-25
> **monkeybrain2012 said:**
> I don't know about disabling journaling, but these flash drives are still alive and working after many rewritings over three years, for something you get for $10 it is more than worthy already. :)

That's good to know, thanks.  It sounds like the talk about 'wearing out' is overstated.  After posting to this thread I did a bit of research and if I have it right, by using ext4 I can enable TRIM and noatime which may help.

---

