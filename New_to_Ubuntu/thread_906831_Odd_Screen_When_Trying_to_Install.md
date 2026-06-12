---
title: "Odd Screen When Trying to Install"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Jinkzt3r on 2008-08-31
Hey guys, I had posted something about this in the General Help forum.. so I hope it is ok that I came here to do so, if not - please delete this post!


Here I go.

Alright. After downloading Ubuntu, check the md5sum and copying the ISO to a CD with ISO Recorder (Version 3, 32-Bit Vista Version) at 9x speed, I popped it into my CD-ROM Drive and began my fifth or sixth attempt at a successful installation of Ubuntu.

Only to get this screen:
[http://img401.imageshack.us/img401/6498/img00018di1.jpg](http://img401.imageshack.us/img401/6498/img00018di1.jpg)


To go back a couple of days...

I had attempted previously to just run Ubuntu through a Dual Boot on a single hard drive (the one I currently have WinXP on, 200 GB) but had gotten the same problem.

I then attempted to try a full install on my second hard drive (80 GB). It seemed to have been working (I did run this one in *safe graphics mode*) and every thing seemed fine. I got my Windows wireless drivers installed, tinkered with some settings, download the add-ons I needed, etc. 

After getting the add-ons I had to reboot, so I did, only to come face to face with this screen once again.

I built my computer myself, to a degree, I kind of already had everything I needed within the tower itself I just had to replace some parts (motherboard, graphics card, RAM, power supply, and CPU).

So I am currently running the following:

Windows XP 
Intel Pentium D CPU 3.20 GHz
1.00 GB of RAM
NVIDIA GeForce 6800
200 GB Hard Drive
80 GB Hard Drive


*I can post more specs if needed? Just ask :P*

I'm not sure if this is truly worth investigating or not, seeing as how it may be a one time problem, but I thought I would throw it out there none the less.

It also wouldn't hurt to find out! I really want Ubuntu to work for me but it's giving a migraine at this point lol.

Thanks again,

Jinkzt3r

---

### Post by appier on 2008-08-31
I had gotten this screen earlier when I attempted to install on an older Compaq with a Pentium 2 to a dual boot system.  When I used only one hard drive and attempted a guided install using all of the disk, the installation went ahead, and I had no problems.

---

### Post by pi.boy.travis on 2008-08-31
When *exactly* do you see this screen?

---

### Post by Pro-reason on 2008-08-31
When does this occur?  Can you manage to use the Live CD?

---

### Post by Jinkzt3r on 2008-09-01
> **appier said:**
> I had gotten this screen earlier when I attempted to install on an older Compaq with a Pentium 2 to a dual boot system.  When I used only one hard drive and attempted a guided install using all of the disk, the installation went ahead, and I had no problems.

Lucky :P, I've tried a guided install on either of my hard drives and still, this screen. Very odd.

> When exactly do you see this screen?
It's very odd, it generally happens after the load bar when I hit "Install Ubuntu," and at other times it happened after the load bar when I rebooted after already having Ubuntu installed and running and just needed to do a quick restart due to updates and so forth.

> 
When does this occur? Can you manage to use the Live CD?
I have been using the LiveCD (I thought? Burnt the ISO image on to a disc and used that to attempt an install?) as well as having attempted running it straight from Windows desktop, and I get the same screen.

---

### Post by stalkingwolf on 2008-09-01
Have you tried booting into recovery mode and reconfiguring xserver?

sudo dpkg-reconfigure xserver-xorg

---

### Post by Jinkzt3r on 2008-09-01
I have tried booting in recovery mode, but either this screen comes up again or it just doesn't work (can't remember specifics here, was a few days ago I tried that :P). Although, I didn't try the reconfiguration.. but I will if I can some how get into ubuntu with recovery mode, thanks!

---

### Post by pi.boy.travis on 2008-09-01
Just to double check, did you perform the "check CD for defects" step in the boot menu of the CD you used to install?  Even if you do that, there is still a chance something could be worng.  You might want to just burn a new CD and give it another go.

---

### Post by Jinkzt3r on 2008-09-01
> **pi.boy.travis said:**
> Just to double check, did you perform the "check CD for defects" step in the boot menu of the CD you used to install?  Even if you do that, there is still a chance something could be worng.  You might want to just burn a new CD and give it another go.

I did and it turned out fine, and I've already burned three different CDs heh??

---

