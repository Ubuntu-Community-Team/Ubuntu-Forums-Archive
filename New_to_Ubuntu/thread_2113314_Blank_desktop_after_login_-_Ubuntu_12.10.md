---
title: "Blank desktop after login - Ubuntu 12.10"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Cohbalt on 2013-02-07
Hi all, first of all I'm *completely* new to Ubuntu. I really wanted to learn/be familiar with Linux but didn't want to install it as a main OS so I decided to use VirtualBox to play around with it.

First time around I installed the 64bit version but I kept getting the kernel error. I couldn't find the option to enable Intel Virtualization Technology in my BIOS so I just downloaded the 32bit version instead.

I didn't see anything obviously wrong with the installation, but whenever I login (the login screen appears to be normal) I'm presented with a blank desktop. I see the background color/image but there are no icons. 

I tried reinstalling it but I got the same results.

**Details:**
Host OS is Windows 7 64bit
VirtualBox version 4.2.6
giving the virtual machine ~1gig of ram and and 8 Gigabyte HDD
Gfx card - GTX 670

Please let me know if there's any more information I should be providing. 

Thank you! :D

---

### Post by Cohbalt on 2013-02-07
Also, often times when I restart the machine it hangs on the black screen right after "Checking battery state  [OK]"

Or after "Starting"

---

### Post by sandyd on 2013-02-07
> **Cohbalt said:**
> Hi all, first of all I'm *completely* new to Ubuntu. I really wanted to learn/be familiar with Linux but didn't want to install it as a main OS so I decided to use VirtualBox to play around with it.

First time around I installed the 64bit version but I kept getting the kernel error. I couldn't find the option to enable Intel Virtualization Technology in my BIOS so I just downloaded the 32bit version instead.

I didn't see anything obviously wrong with the installation, but whenever I login (the login screen appears to be normal) I'm presented with a blank desktop. I see the background color/image but there are no icons. 

I tried reinstalling it but I got the same results.

**Details:**
Host OS is Windows 7 64bit
VirtualBox version 4.2.6
giving the virtual machine ~1gig of ram and and 8 Gigabyte HDD
Gfx card - GTX 670

Please let me know if there's any more information I should be providing. 

Thank you! :D
Few things to check - Have you checked the graphical settings for Virtualbox?

They are under Virtual Machine Settings -> Display -> Enable 3D Video Acceleration. Increasing the amount of video memory can't hurt either ;)

---

### Post by Cohbalt on 2013-02-07
Enabled 3D Acceleration and have allotted 32MB of video memory to it. No change :(

Also, whenever I try to "Send the shutdown signal" it doesn't seem to shut off (or I'm just not patient enough), I have to "Power Off" the machine. It doesn't like that very much and as I mentioned it tends not to boot up afterwards, instead getting stuck on the "Checking Battery State".

---

### Post by Cohbalt on 2013-02-08
Any other suggestions?

---

### Post by MadmanRB on 2013-02-08
Eh I have had issues with 12.10 in virtualbox, it reallky is a crap release.
I would go with 12.04 LTS, far more stable and you can still get newer packages in it via ppa's

---

### Post by Cohbalt on 2013-02-09
Hey that did that trick! Thank you! :)

Also, how do I correct the screen? Even if I select "Full screen" in VirtualBox it just makes the icons bigger and bloated.

---

