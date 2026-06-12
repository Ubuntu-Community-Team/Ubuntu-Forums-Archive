---
title: "How do I upgrade 11..10 to 12.10 (Wubi.exe doesn't run in Ubuntu)"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by RedOctober on 2012-11-26
I have several machines running Ubuntu 11.10, latest updates.  I want to update them all to 12.10 now.  However the only CD image .iso download I can get is the one that has wubi.exe on it.  My understanding is that is the CD you would use if you wanted to CONVERT an existing Windows machine to an Ubuntu machine.  I need the .iso that will run on an existing Ubuntu 11.10 machine and allow it to upgrade to Ubuntu 12.10.  Where is the correct .iso image for a CD that will allow me to do this?

Alternatively, is there an "on-line" way I should be upgrading these machines?  All I can see in the Update Manager now, is an "upgrade" to 12.04 LTS" which I don't really need nor want.

Thanks in advance for any help you can provide.

---

### Post by Wim Sturkenboom on 2012-11-26
You can not directly upgrade from 11.10 to 12.10. You have to do every step: 11.10 -> 12.04 -> 12.10.

---

### Post by squakie on 2012-11-26
+1.  From that release, your best bet to upgrade without running into problems is to back up everything you need (perhaps your data is on a separate partition, perhaps /home?).  Then download the 12.04 or 12.10 ISO, burn it to a DVD and then completely reinstall Ubuntu.  Otherwise you stand a big chance of getting old and new libraries, etc., mixed and all kinds of weird things happen.

---

### Post by mlentink on 2012-11-26
> **RedOctober said:**
> However the only CD image .iso download I can get is the one that has wubi.exe on it.  My understanding is that is the CD you would use if you wanted to CONVERT an existing Windows machine to an Ubuntu machine.
Just to make sure, you were ***booting*** from this cd/dvd? 
> **RedOctober said:**
> All I can see in the Update Manager now, is an "upgrade" to 12.04 LTS" which I don't really need nor want.
Yes you do. As per Wim Sturkenboom's reply above, you will want to upgrade to 12.04 first, en then to 12.10

---

### Post by audiomick on 2012-11-26
+1 you need to go through 12.04. The upgrader will only do one version at a time. The only apparent exception is that it will do one LTS to another, i.e. you would be able to go from 10.04 direct to 12.04, and from there to 14.04 when it comes out.

If you want to use the upgrader, it is, from what I have read, a good idea to disable any PPA's you might have active before you start. Your best chance of a clean upgrade is with a bog standard Ubuntu install. The more you have "improved" it, the more likely that the upgrader will get confused.

If you want to go directly to 12.10, you only option is, as squakie suggested, to do a fresh install. This may even be the quicker option. The upgrader can take a while.


Whatever you do, backups before you start is always a good idea.

---

### Post by newb85 on 2012-11-26
> **RedOctober said:**
> I have several machines running Ubuntu 11.10, latest updates.  I want to update them all to 12.10 now.  However the only CD image .iso download I can get is the one that has wubi.exe on it.

Upgrading using Live CD/DVD/USB would not be a bad idea, since you're doing several machines.  It would save downloading the same thing over and over.  12.10 is not available as a CD; you'll have to go with DVD or USB.  As already stated, you should upgrade to 12.10 via 12.04.

Wubi.exe is *not* a CD image.  It's the Windows installer.  And I don't think it will do you any good.  Why would that be all you can get your hands on?

---

### Post by RedOctober on 2012-11-26
Ok, here's my problem.  In Firefox, Google, I type "ubuntu bootable cd image",  the page I select is:  

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

then

[http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=32&release=latest](http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=32&release=latest)

then

[http://www.ubuntu.com/download/desktop/thank-you?release=latest&bits=32&distro=desktop&status=zeroc](http://www.ubuntu.com/download/desktop/thank-you?release=latest&bits=32&distro=desktop&status=zeroc)

That downloads a file called  ubuntu-12.10-desktop-i386.iso

Which, when burned (as an "image") to CD/DVD creates the wubi.exe file on the CD along with a bunch of other files.    My laptop with a newly formatted blank hard drive, set in BIOS to boot from the DVD cannot boot from this CD because it's not a bootable image, it's just a CD with wubi.exe on it, which needs to be run by a Windows machine.

I am looking for the .iso that will produce a bootable CD/DVD that will allow me to install Ubuntu 12.10.

Am I going to the wrong website for this download?  I've been searching for hours but all my searches end up taking me to the exact same page, with the exact same WUBI.exe CD, which can't be used as a bootable CD from a computer with no OS.  (There is no data on the computer)

---

### Post by audiomick on 2012-11-26
That is sounding a bit odd.

The pages you linked to are the right ones to get a bootable CD. Incidentally, I believe that there is a WUBI.exe on the live CD, although I am not sure. Anyway, the .iso that you get from the last link should be the right one. 

Did you do a md5[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")sum on the .iso?

Have you something else bootable to see if the machine will, in principle, boot from the DVD drive? If not, maybe you could organise something?

Perhaps you could try putting the installer on a USB stick instead of the CD...
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Just for the record, what are you using to burn the image to a CD?

---

### Post by arpanaut on 2012-11-26
> **RedOctober said:**
> Ok, here's my problem.  In Firefox, Google, I type "ubuntu bootable cd image",  the page I select is:  

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

then

[http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=32&release=latest](http://www.ubuntu.com/download/desktop/questions?distro=desktop&bits=32&release=latest)

then

[http://www.ubuntu.com/download/desktop/thank-you?release=latest&bits=32&distro=desktop&status=zeroc](http://www.ubuntu.com/download/desktop/thank-you?release=latest&bits=32&distro=desktop&status=zeroc)

That downloads a file called  ubuntu-12.10-desktop-i386.iso

Which, when burned (as an "image") to CD/DVD creates the wubi.exe file on the CD along with a bunch of other files.    My laptop with a newly formatted blank hard drive, set in BIOS to boot from the DVD cannot boot from this CD because it's not a bootable image, it's just a CD with wubi.exe on it, which needs to be run by a Windows machine.

I am looking for the .iso that will produce a bootable CD/DVD that will allow me to install Ubuntu 12.10.

Am I going to the wrong website for this download?  I've been searching for hours but all my searches end up taking me to the exact same page, with the exact same WUBI.exe CD, which can't be used as a bootable CD from a computer with no OS.  (There is no data on the computer)

From the first link in your post just below the 12.10 offering is a link for the 12.04 iso.
scroll down the page and on the right are instructions on how to produce bootable media.
be sure to choose the correct iso for the architecture of your system, 32 bit, 64 bit and if you are just trying to upgrade be sure it matches what you already have installed.
I have been offered an upgrade from just inserting the iso media on my installed system, but generally one would boot from cd/dvd/usb media and follow the prompts to achieve desired results.

---

### Post by RedOctober on 2012-11-26
The link you describe is for the Long Term Service version, 12.04.  I'm after the free version, version 12.10.   I need the .iso that can create an Ubuntu 12.10 install onto a blank hard drive on a computer with no operating system.  The way it is now... I have to install Windows, before I install Ubuntu, so that the wubi.exe will run.

---

### Post by arpanaut on 2012-11-26
Both are Free!
As said before you will either need to reinstall to 12.10 or upgrade from 11,10 > 12.04 > 12.10.
One can upgrade from LTS > LTS but the interim releases have to be upgraded sequentially.

---

### Post by mlentink on 2012-11-26
> **RedOctober said:**
> The link you describe is for the Long Term Service version, 12.04.  I'm after the free version, version 12.10.   I need the .iso that can create an Ubuntu 12.10 install onto a blank hard drive on a computer with no operating system.

All Ubuntu versions are free, always have been.

Edit: Whoops! Always turn the page...

---

### Post by grahammechanical on 2012-11-26
This morning I downloaded an ISO image of Raring Ringtail 13.04 for testing. It also has wubi.exe on it.

What is the problem? The ISO image sizes are now too big to fit on a CD disk. We have to use a DVD disk. This allows more stuff to be included in the ISO image.

Also, a decision has been taken to reduce the number of ISO images available. You will not find alternate ISO images for 12.10. I would guess that the separate ISO containing wubi.exe has also been discontinued.

Or to put it another way, the image for installing in Windows (wubi) has now been blended into the standard Ubuntu ISO image. Do not forget that wubi is a Windows application. You run it from Windows as you run any other Windows application that you want to install.

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Regards.

---

### Post by mlentink on 2012-11-26
Once again, you downloading the correct iso which, when burned correctly, leads to a bootable dvd (the image is too large for a cd).

Another thing you could try is to boot with a USB-stick, as per the instructions here: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

