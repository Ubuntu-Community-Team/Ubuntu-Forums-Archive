---
title: "Acer Aspire 3630, SiS M661MX"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by thomaskaiserfn on 2013-11-28
I just wanted to install ubuntu 12.04.3 via CD (from ubuntu.com) on a outdated Aspire 3630.

Acer Aspire 3633WLMI
Intel Celeron M processor 370
(1,5 GHz, 400 MHz FSB, 1MB L2 cache)
15,4" WXGA CrystalBrite TFT LCD
60GB HDD
DVD-Dual
(support DVD+R Double Layer/DVD+-RW)
512MB DDR
802,11b/g wireless LAN

First partition with NTFS, second with FAT32, because i don´t have enough space for a full formatting.


The installation worked pretty well, but after it says "preparing for first start" or something, the screen flickers and there is temporarily a cursor in the middle.
It seems the machine has graphicproblems and the screen is shuting off and on frequently.

I installed Windows XP and tried to install ubuntu as additional OS. Windows is working perfectly, but I got the same error for ubuntu after the reboot.
(Xubuntu, Lubuntu etc. don´t seem to make a difference.)

This is the first time I worked with this OS and I have absolutely no clue what to do about this.
Some ideas??

---

### Post by mörgæs on 2013-11-28
Hi, welcome to the fora.

You might have a problem with SIS graphics. Are you able to run any of the distros in a live boot?

---

### Post by thomaskaiserfn on 2013-11-28
Actually I don´t know what a live boot is... is this the installation on a virtual machine?!

---

### Post by heir4c on 2013-11-28
That is when you boot from the live-cd or live-usb where the .iso file is put on to start the live-session.
How you install Ubuntu? From IN Windows or from a cd or usb?
If you can put more RAM in. (a total of 1GB or more is better to run the system on).

---

### Post by heir4c on 2013-11-28
Have you a SIS graphics, than here a possible solution:
[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)
(Only for Lubuntu and Xubuntu)

---

### Post by thomaskaiserfn on 2013-11-28
Oh okay, I think I tried starting from the live-cd as well. The Problem is always the same.
I have tried installing it on a complete formatted partition and after the windows-setup IN windows for testing purposes.

I don´t have spare RAMs to assemble and I would like to avoid spending money if it is any possible.

Is there a way to install something like drivers?

---

### Post by mörgæs on 2013-11-28
The live boot was not requested for installing, but for running the command

```
sudo lshw -sanitize > lshw.txt
```

When you have done that please post lshw.txt in CODE tags.

---

### Post by heir4c on 2013-11-28
What graphics card have you? 
If it is a SIS than look to my previous post for the link. 
If not, than post here what card you have.

---

### Post by thomaskaiserfn on 2013-11-28
> **heir4c said:**
> Have you a SIS graphics, than here a possible solution:
[https://sites.google.com/site/easylinuxtipsproject/sis](https://sites.google.com/site/easylinuxtipsproject/sis)
(Only for Lubuntu and Xubuntu)

Piew, how can I check if I have a card like such.
I don´t think I have found anything like a graphic-card in the windows hardware manager.

---

### Post by heir4c on 2013-11-28
Type the command who mörgæs give, in a terminal, like he asked. Than we can see what graphics you have.
ThanX

---

### Post by thomaskaiserfn on 2013-11-28
I found something named "SiS M661MX" in the Hardwaremanager. Is this what you were looking for?

(I have absolutly no idea where to type in the commands.. oO)

---

### Post by mörgæs on 2013-11-28
It was what I feared, yes. 
There are workarounds available but I don't have experience with them. [Bodhi Linux]("http://www.bodhilinux.com/") might be an option.

---

### Post by thomaskaiserfn on 2013-11-28
> **mörgæs said:**
> [Bodhi Linux]("http://www.bodhilinux.com/") might be an option.

Thank you, I am going to try that. :)

---

### Post by thomaskaiserfn on 2013-11-28
I think i struggle a bit with this [installation instruction]("http://wiki.bodhilinux.com/doku.php?id=installation_instructions").
But I got audio and video failures in live-mode anyway. :(

---

### Post by heir4c on 2013-11-29
In your link there mensioned something about nomodeset. See under "II: Boot into the Live Environment".
There see you:
> Some users may have to select the xForcvesa or nomodeset option, depending on the video card. The only way to know for sure is to try and see.
So you can choose that to start it so it would not have problems with the graphics because it uses basics settings for the graphics.
Try it out.

---

