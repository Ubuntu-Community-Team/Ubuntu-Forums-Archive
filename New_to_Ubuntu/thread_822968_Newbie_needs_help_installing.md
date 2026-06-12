---
title: "Newbie needs help installing"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by umopapisdn on 2008-06-08
I am trying to install ubuntu for the first time but it seems to be freezing (or else VERY slow) .. the install window has come up but no icon (which I expect from the docs to be able to click).

I am using an older machine and hoping to install it without keeping a windows partition. I have booted from the CD.

Anyone around who wants to chat/talk me through this?

---

### Post by spiderbatdad on 2008-06-08
Do you have at least 512 Ram? If you only I 256, you would be better off with a lighter version...Xubuntu.
You should see installations options after starting with the live cd. Have you checked the integrity of the cd?

---

### Post by oilchangeguy on 2008-06-08
> **umopapisdn said:**
> I am trying to install ubuntu for the first time but it seems to be freezing (or else VERY slow) .. the install window has come up but no icon (which I expect from the docs to be able to click).

I am using an older machine and hoping to install it without keeping a windows partition. I have booted from the CD.

Anyone around who wants to chat/talk me through this?

define older computer. specs please. and ubuntu version you're using.

---

### Post by umopapisdn on 2008-06-08
The system is:
Intel(R) Celeron (R) CPU 1.70 GHz, 248 MB of RAM
It says its a ACPI Uniprocessor PC
It has an AOPEN CD-RW CRW4850
It has an IDE controller for a Maxtor 38.1 GB drive 


The version of ubuntu is: Ubuntu 8.04 LTS Desktop Edition

---

### Post by umopapisdn on 2008-06-08
Yes, checked the CD integrity -- but no, not 512 RAM -- so maybe I should be looking for xubuntu?

---

### Post by spiderbatdad on 2008-06-08
> **umopapisdn said:**
> Yes, checked the CD integrity -- but no, not 512 RAM -- so maybe I should be looking for xubuntu?

Definitely, if ubuntu is your choice of distro.
You may find that you are going to have to experiment with a few boot parameters to get the live cd to start on that machine.

If it doesn't boot to desktop, you will need to press F6 from the install options screen, and delete --quiet splash from the end of the boot line.
Replace that with noapic nolapic

There are other options described by pressing F3 (?) after F6...try to follow the dialogue, and you'll get it.

I tried my hand at a blog on boot parameters for ubuntu, as I haven't found much, searching the internet...at least not much that wasn't overwhelming.
[http://spiderbatdad.wordpress.com/ubuntu-boot-problems/](http://spiderbatdad.wordpress.com/ubuntu-boot-problems/)

That blog needs help. I'll try rewriting it soon, but it should help you, if you have booting problems.

---

### Post by umopapisdn on 2008-06-08
Thanks so much. I appreciate your help.

---

### Post by umopapisdn on 2008-06-08
Okay. So now I have downloaded xubuntu (v 7.10) and I get an "I/O Error reading boot CD." message when I try to check the integrity of the CD. Some green digits come up on top of the screen -- it's hard to tell if they are upsidedown? maybe AA4ZAADF / upsidedown 36ADZDAN ?

---

### Post by SunnyRabbiera on 2008-06-08
actually try the hardy version of xubuntu, or try to install regular ubuntu in safe mode.
On the ubuntu live CD you can try to use the second mode down.

---

### Post by Xiong Chiamiov on 2008-06-09
The alternate CD uses a command-based interface, and is much easier to use on lower-end systems.

Xubuntu will be easier to run on a system like that, as far as the *buntus go.  If it's too slow for your tastes, you could try Fluxbuntu, or one of many, many other lightweight window managers.

---

### Post by spiderbatdad on 2008-06-09
> **umopapisdn said:**
> Okay. So now I have downloaded xubuntu (v 7.10) and I get an "I/O Error reading boot CD." message when I try to check the integrity of the CD. Some green digits come up on top of the screen -- it's hard to tell if they are upsidedown? maybe AA4ZAADF / upsidedown 36ADZDAN ?

Sounds like it didn't verify...in other words, either the burn was bad or the iso you started with...a real drag. Sorry. Remember to burn the iso at the slowest possible speed.

Do you know how to check md5sums before and after burning the disk? It isn't too hard:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Scroll down to the section on Windows, if you are currently running windows and try to make the image from there. So, don't use the disk check utility from the install options screen...just proceed with previous instructions regarding boot parameters.

---

### Post by umopapisdn on 2008-06-09
> **spiderbatdad said:**
> Sounds like it didn't verify...in other words, either the burn was bad or the iso you started with...a real drag. Sorry. Remember to burn the iso at the slowest possible speed.

Do you know how to check md5sums before and after burning the disk? It isn't too hard:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Scroll down to the section on Windows, if you are currently running windows and try to make the image from there. So, don't use the disk check utility from the install options screen...just proceed with previous instructions regarding boot parameters.

Okay. The checksum is verified so I am trying to burn it more slowly and see if that fixes things up. I am burning the CD on one computer (my laptop which is running Windows XP) and then trying to use it in another (older desktop machine).

---

### Post by oilchangeguy on 2008-06-09
> **umopapisdn said:**
> The system is:
Intel(R) Celeron (R) CPU 1.70 GHz, 248 MB of RAM
It says its a ACPI Uniprocessor PC
It has an AOPEN CD-RW CRW4850
It has an IDE controller for a Maxtor 38.1 GB drive 


The version of ubuntu is: Ubuntu 8.04 LTS Desktop Edition

your computer is not that bad. the problem is the amount of ram. you'd do yourself a big favor if you'd install more. my guess is the computer probably supports 1gb of ram. 512x2.

---

