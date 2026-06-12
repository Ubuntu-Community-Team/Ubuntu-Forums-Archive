---
title: "PC will not install Windows, but will Ubuntu ..."
date: 2011-11-09
forum: New to Ubuntu
---

### Post by cwmoser on 2011-11-09
A friend asked me to fix her Windows XP computer.  It crashes before fully booting and then reboots.  I tried CDROM booting with my PE Boot disk and that crashes.  I tried Ubuntu CDROM and was successful.

Hmmm.  So I replace all her RAM memory (2GB) and replace her Hard Drive.  Tried to install Windows XP but I got the Blue Screen on two attempts. 

Then I took my 11.04 Ubuntu CDROM and successfully loaded Ubuntu. 

Apparantenly the problem is with the Motherboard as I replace both her RAM and HD.  Some feature with the Motherboard is not working for Windows.

So my question is what is it with a Motherboard that allows Ubuntu to be installed but will not allow Windows?  Please no smart a$$ responses - I find this very unusual.

Carl

---

### Post by fantab on 2011-11-09
> **cwmoser said:**
> A friend asked me to fix her Windows XP computer.  It crashes before fully booting and then reboots.  I tried CDROM booting with my PE Boot disk and that crashes.  I tried Ubuntu CDROM and was successful.

Hmmm.  So I replace all her RAM memory (2GB) and replace her Hard Drive.  Tried to install Windows XP but I got the Blue Screen on two attempts. 

Then I took my 11.04 Ubuntu CDROM and successfully loaded Ubuntu. 

Apparantenly the problem is with the Motherboard as I replace both her RAM and HD.  Some feature with the Motherboard is not working for Windows.

So my question is what is it with a Motherboard that allows Ubuntu to be installed but will not allow Windows?  Please no smart a$$ responses - I find this very unusual.

Carl

How do you know that the Disk you are using to install is not corrupt? What makes you sure that the software XP you have is not corrupt? Have you tried another copy of XP? 
Have you updated the BIOS version? Sometimes the Old BIOS version may not adapt to the Hardware changes. 

This happened to me once. The same disk with XP would install without any issues on my Desktop but would not install on my friend's Lenovo notebook, crashing every time with a BSOD. The Error report said that some files were missing. When we tried another XP disk from another source it just installed without any problem. 

What is the make of Motherboard, by the way?

---

### Post by Mark Phelps on 2011-11-10
One possibility is that the hard drive in the PC is connected via a SATA port, not IDE, and the XP disk is an original version, and does not have the proper SATA drivers.  The Ubuntu CD is a lot newer and WOULD have the proper SATA drivers.

That said, if it's not getting far enough in the installation to allow you to press F6 to load SATA drivers, then my guess could be wrong.

Does the drive show up properly in the BIOS messages when the PC boots?

---

### Post by Deanobats on 2011-11-10
This is basically the reason that I ended up with Ubuntu. I had a Dell laptop where the XP installation died. I tried reinstalling XP, but the install disk kept giving me the blue screen of death. My understanding of one of the reasons that this can happen is that I had an old XP install disk, and for the sata drive on the laptop I needed one with Service Pack 2 on it as well. I could run Ubuntu from a live cd and access the hard drive so got all my old files off the laptop, then went ahead with the Ubuntu install, which went fine. So here I am!

---

### Post by snowpine on 2011-11-10
I like bashing Windows as much as the next guy :) but I think to be fair, you should try a legally-purchased install CD of the current release before making any definitive "Windows vs Ubuntu" comparisons.

An analogy is if someone came on these forums with problems installing Ubuntu 4.10 Warty Warthog. I would encourage them to download the current 11.10 release, check the MD5SUM of the CD, and try again. :)

---

### Post by dFlyer on 2011-11-10
If the owner wants XP, why not try a Windows XP Forum, they may be able to provide better support concerning hardware. Sounds like linux works good, so it's not a linux issue. The above answer about hardware drivers causing the problem from an old XP version sound the best.

---

### Post by Swagman on 2011-11-10
It could well be the XP SP1 disk you have (no sata) but you should have a floppy somewhere with the sata drivers on it or they are on the Motherboard resource disk.

Or.. It could be that your CD/DVD ROM doesn't like that disk. Don't laugh.. It really happens. In which case you could try jury rigging another cd/dvd and try installing XP from that.

---

### Post by Mark Phelps on 2011-11-10
Another possibility, although less likely, is if the CD is one of the original XP version, the CD could simply have degraded over time.

Really -- CDs don't last forever.

So, if there is another PC available, I would try cloning the XP CD to a new blank CD.  That will eliminate any media-based problems.

---

### Post by sadaruwan12 on 2011-11-10
> **Swagman said:**
> It could well be the XP SP1 disk you have (no sata) but you should have a floppy somewhere with the sata drivers on it or they are on the Motherboard resource disk.

Or.. It could be that your CD/DVD ROM doesn't like that disk. Don't laugh.. It really happens. In which case you could try jury rigging another cd/dvd and try installing XP from that.

Swagman is correct that happens to me but best thing is to do read the error code given by the BSOD and google it I managed to solve lot of issues by doing that.

In my experience motherboards don't give much trouble if they do that issue will be the same for any OS.

---

### Post by drmrgd on 2011-11-10
Knowing what the BSOD error actually is would be very helpful.  Googling it or posting it here would e very informative.  

In my experience, if you don't have the SATA drivers, Windows just says that it can't find a hard drive in the system to install to.  There's no BSOD really.  I like the idea about the CD-ROM being degraded, though.  I'll bet that's what's going on.

---

### Post by sadaruwan12 on 2011-11-10
> **drmrgd said:**
> Knowing what the BSOD error actually is would be very helpful.  Googling it or posting it here would e very informative.  

In my experience, if you don't have the SATA drivers, Windows just says that it can't find a hard drive in the system to install to.  There's no BSOD really.  I like the idea about the CD-ROM being degraded, though.  I'll bet that's what's going on.

You might be correct 'cos in my early career as an Hardware Technician I've come across lot's of issues just like these.

---

### Post by cwmoser on 2011-11-10
I tried to install Windows XP on this PC using two different legal Win XP CDROMs.  I tested the CDROM by installing Windows on another PC with a Sata hard drive and it successfully installed.  I highly suspect that there is a malfunction with the MB but does not affect Ubuntu.  Not the first time I have seen this, but it rarely happens like this.

Carl

---

