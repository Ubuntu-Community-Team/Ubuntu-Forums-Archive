---
title: "Instalation issues"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by alexvision on 2008-11-06
First off I'd like to let everyone know that I'm a complete noob at this, and have never installed Linux before this, so please be nice to me I'm still learning.

OK, so I downloaded 8.10 and burnt it to a cd, the cd works fine and I have booted it up as a live cd. I tried to do this with another older computer (2001-2002ish)and it started to load, but stopped on about the third bar. I'm guessing that this is a driver issue?? anyways any Ideas on how to fix it. Its a hand-me-down so I'm not too sure whats in it but It has a pentium4 solo @2.0ghz, about 30gb ide hdd, old nVidia gpu (gforce 4 series or earlier) and an unnamed mobo with half a gig of generic ram. 

I'm not too sure of the details, but I will take a look if needed. 

Thanks in advance 

Alexvision

---

### Post by billgoldberg on 2008-11-06
> **alexvision said:**
> First off I'd like to let everyone know that I'm a complete noob at this, and have never installed Linux before this, so please be nice to me I'm still learning.

OK, so I downloaded 8.10 and burnt it to a cd, the cd works fine and I have booted it up as a live cd. I tried to do this with another older computer (2001-2002ish)and it started to load, but stopped on about the third bar. I'm guessing that this is a driver issue?? anyways any Ideas on how to fix it. Its a hand-me-down so I'm not too sure whats in it but It has a pentium4 solo @2.0ghz, about 30gb ide hdd, old nVidia gpu (gforce 4 series or earlier) and an unnamed mobo with half a gig of generic ram. 

I'm not too sure of the details, but I will take a look if needed. 

Thanks in advance 

Alexvision


I'm sure it's a driver issue, it could just be that the pc isn't powerfull enough to run the live cd.

If you want to install Ubuntu on it, download the alternate cd and use that install it (that isn't a live cd, and it gives a text interface installer).

---

### Post by bennachie on 2008-11-06
There should be no problem running the LiveCD on the setup you have described. I have a spare machine of the same vintage (with the equivalent AMD CPU and what sounds like the same graphics cards, but with three miscellaneous IDE hard disks) and have had no real problems apart from the infamous "busybox+initramfs" issue, which I have worked around.

How much of the 30GB hard disk is occupied by the existing OS (and what, exactly, is the OS in question). Are you getting any error messages, or does the disk hang without explanation? Have you tried a direct install without running the LiveCD?

---

### Post by bumanie on 2008-11-06
I would suggest you download the alternate install cd and install with that. It is text-based and 99% of the time will install on to a machine that has issues with the live cd.

---

### Post by Kevbert on 2008-11-06
Welcome to Ubuntu. It may be worth performing a memory check, you can do this via the installation CD menu.  When the PC stops loading 'after the third bar' do you leave it for a little while (as the operating system is being loaded into memory) ?
Did you perform a hash check on the ISO file that you downloaded ? Information on how to check this can be found [[COLOR="Red"]here.[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") Have you checked the CD integrity (via the menu option) ?
Your PC should work with Ubuntu with 512Mb, but may run slowly. A better bet would be to use [[COLOR="Red"]Xubuntu.[/COLOR]]("http://www.xubuntu.org/get").

---

### Post by cmittle on 2008-11-06
I agree with the Xubuntu.  I found an emachines on the curb during spring clean up a few years ago and I dropped a hard disk in it and now it's my server.  Xubuntu is nice and lightweight which should make installation a little easier/faster.  After you have that installed you can install the LXDE desktop environment if you'd like.  From my experience on my desktop and laptop that boots even faster than XFCE (Xubuntu).

Also, as Kevbert mentioned you should check the integrity of the data.  Sometimes it seems people just have a bad download or burn of the LiveCD.

Good luck, and don't forget you will keep learning after you have it installed too.

---

### Post by alexvision on 2008-11-07
I don't think that it is a corruption issue, as I have been able to boot from several other computers, its a driver issue, as the computer meets the minimum requirements. If so how would I go about fixing this, or if I installed it onto the hard drive would it work?? 
Thanks For the suggestions 
Alexvision

---

### Post by alexvision on 2008-11-07
I'll try out xubuntu, but at the moment I'm trying to find a solution cause I really don't want to use more of my downloads than I have to :( 

any other ideas would be great 

Thanks

---

### Post by CrazymanBrad on 2008-11-07
You may want to try version 8.04.  I just installed 8.10 on two computers that were running 8.04, but now they both have various problems - drivers, reboot problems, shutdown problems.  None of these were issues with 8.04.  I think 8.10 needs a bit of fermenting before it's ready for mass public consumption.

---

### Post by pgorillaman on 2008-11-07
I had the same problem and it turned out to be a driver issue with the nvidia driver. I went ahead and installed and then booted to cmd prompt and edited the xorg.conf file. Not recommended for the new user. I would do as previous posters suggested and install 8.04.

---

### Post by alexvision on 2008-11-09
I've tried booting xubuntu and ubuntu 8.4 even trying DSL to no avail. A friend mentioned about changing the apic or something similar, but I can't remember which ones he said to try, so I tried most of them, in most combinations with no luck, I'm not sure what to try next (and I did check each distro to see if it was working on other pc's which it was) Any other ideas, or any suggestions on how to get the drivers, or find out which ones I need. 

EDIT; would ubuntu work if it was installed straight onto the hard drive, even if it doesn't work as a live cd??

---

