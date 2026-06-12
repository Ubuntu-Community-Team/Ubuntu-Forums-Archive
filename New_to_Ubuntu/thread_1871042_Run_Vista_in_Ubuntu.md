---
title: "Run Vista in Ubuntu?"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by Rory 000 on 2011-10-28
Hi everyone, first post from a newby to Ubuntu via 11.10.


The short version; my Sony Vaio VGN-FW21l fell on its own sword, taking Vista with it. The backup disks are nowhere to be found (I told my wife clearing the attic was a bad idea, but would she listen?).

So here I am with 11.10 and Chromium, and I love it. It's difficult to believe it's the same hardware - this is just so fast.

Anyway, to the point. There are some things that I just need MS for - my kids maths teachers' CD ROMs for example, encrypted films (medibuntu didn't do the trick), and yes I like itunes. I've seen Vista Business edition (still in the wrapper) on ebay for £35. My knowledge of computers will become apparent in the next couple of sentences (ie zilch). Is it possible to install windows on my external hardrive* and boot Vista from it when I want it? I have a monitor from my old Evesham desktop which also had had enough and took the honourable way out - it would be pretty good if I could fix it up so that I had Ubuntu on this screen and Vista on that, but I guess that would be asking too much????

I apologise if this has been covered, but I couldn't find anything by searching the forum. 
If any of this is not possible and dual boot is the way to go then I'll be happy with that,I've found an online tutorial for it - just thought I'd ask,

Thanks very much for taking the time to read this far :)

Rory. 

*the hard drive is a 1TB seagate which I used to keep the files I saved from the laptop via the live disk version of Ubuntu.

---

### Post by Paqman on 2011-10-28
You could install Windows onto the internal hard drive if you want, running it from an external would be pretty slow. There's no real problem having two operating systems on one machine, you'll just get a menu pop up when you turn it on asking which you'd like to boot.

You would need to open up Disk Utility and make a new partition on your hard drive. Easiest thing to do would be format it as NTFS. The boot the Windows install disk and install to that partition. Afterwards you would need to [restore Ubuntu's bootloader]("https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu"), as Windows will (rather rudely) kill it when it installs.

Voila! A dual-boot system. It would be best to take a backup of the Ubuntu system before starting, just in case something went wrong. You shouldn't have any trouble though, people at this forum can help you with any queries or problems you might have.

Running two operating systems at once is also possible, but requires reasonably punchy hardware (minimum of a dual-core processor and about 4GB RAM). This uses technology called virtualisation, but isn't difficult to set up if your hardware is up to it. Virtualbox is a very good free virtualisation package that's available for Ubuntu.

---

### Post by Frogs Hair on 2011-10-28
Hello and Welcome

Take a look Virtual Machine in the software center or Virtual Box .[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Rory 000 on 2011-10-28
Thanks for you replies. I've just checked and my processor is (copy and paste)

Intel® Core&#8482;2 Duo CPU T5800 @ 2.00GHz × 2 

and I have 3G memory, but I could upgrade, I guess. 

However, from the Virtualbox site, it says  "To install VirtualBox anyway you need to setup a 64-bit chroot environment."

Hrmmm, the learning curve just got a little steeper......


I've taken the plunge and ordered the Vista DVD, it looks like dual boot might be the (slightly) easier option for now.

Thanks very much for your help. :-)

---

### Post by ubu_dynamite on 2011-10-28
> Mixed installations (e.g. Debian/Lenny ships an AMD64 kernel with 32-bit packages) are not supported. To install VirtualBox anyway you need to setup a 64-bit chroot environment. 

That is meant for debian just choose the right version and install or install virtualbox from the repository

---

### Post by Paqman on 2011-10-28
> **Rory 000 said:**
> 
However, from the Virtualbox site, it says  "To install VirtualBox anyway you need to setup a 64-bit chroot environment."

Hrmmm, the learning curve just got a little steeper......


Yeah, don't worry about that. Just download and install the .deb file for Ubuntu (or better yet, add their repository). Then set up a new VM, give it about 2GB of your system's memory and install Vista into it. Vista might struggle a bit with 2GB RAM (maybe, I've not used Vista much) but it should be good enough to run the occasional app you need.

Once you've set up the VM install the "Guest additions" doodad to give you graphics drivers and sort your mouse out so it works seamlessly between the two OSes.

---

### Post by collisionystm on 2011-10-28
Use a 32 bit Windows XP. You will be a lot more satisfied with the speed.

Win Vista and 7 will be slow in virtualbox. You will be frustrated doing what your trying to do with iTunes...etc.

In your Virtual Machine, only allocate 512 mb of ram. The way the memory works in virtual environment is far different than a physical machine. 
And only allocate one CPU and 1 core and DO NOT turn on I/O APIC
Make sure to enable 2D acceleration.

Does anyone you know have Windows 7 PRO or Ultimate? If so, they can enable XP mode (which is free for them ) and you just copy the XP .vhd file off their computer to yours and you can run Windows XP in your virtualbox for free. Just an fyi.....

---

### Post by 3rdalbum on 2011-10-28
> **Rory 000 said:**
> Thanks for you replies. I've just checked and my processor is (copy and paste)

Intel® Core™2 Duo CPU T5800 @ 2.00GHz × 2 

and I have 3G memory, but I could upgrade, I guess. 

3 gigs is fine, even for Vista as a guest.

> However, from the Virtualbox site, it says  "To install VirtualBox anyway you need to setup a 64-bit chroot environment."

That's not correct. Just install Virtualbox and install Vista within it, easy as pie. I have Vista in a virtual machine on a 64-bit Ubuntu, it certainly doesn't require a 64-bit chroot environment.

---

### Post by Rory 000 on 2011-10-28
> **3rdalbum said:**
> 3 gigs is fine, even for Vista as a guest.



That's not correct. Just install Virtualbox and install Vista within it, easy as pie. I have Vista in a virtual machine on a 64-bit Ubuntu, it certainly doesn't require a 64-bit chroot environment.


Thanks all.

The virtualisation thingumyjig was what I was really asking about - I remember reading about it some time ago, I just couldn't recall enough about it to phrase my question properly.

If it is appropriate I could post a blow by blow account of the setting up process once the Vista DVD gets here - it may help others in the same boat at a later date, and me being a complete novice might show that it's possible to do this without having to know what a chroot environment is :)

---

