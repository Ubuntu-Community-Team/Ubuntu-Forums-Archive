---
title: "First install"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Gemius on 2011-09-28
I am keen to try Ubuntu and have a new empty Formatted drive installed on my computer.
I've looked at all the options for installing and would like to know what if any are the drawbacks of just downloading Ubuntu onto this new disk?

---

### Post by arochester on 2011-09-28
If the drive has no OS on it how are you going to download Ubuntu?

---

### Post by mörgæs on 2011-09-28
Hi, welcome to the fora.

It is not enough to download the ISO file. It must be used as a basis for creating a bootable USB stick or CD, from which you can do the actuel install.

---

### Post by Gemius on 2011-09-28
Thank you for your  replies.
I'm afraid I wasn't very clear. I'll try again. 
 
I have Vista on my first drive and have downloaded Ubuntu to a disk. If that is loaded into my second drive is that all I need to do? 
 
Obviously there will be a set up process and I will want the computer to boot into Windows as others use the computer and they won't want to know about Ubuntu until I've ironed it out.
 
The only problem I can see is when I want to use Ubuntu I will either have to boot into the BIOS and select the second drive or perhaps I could run it by selecting the drive in My Computer.
 
If this will work it seems to me to be the simplest, no fuss way of doing it. If we like it I'll get rid of Windows and if not I can easily remove Ubuntu.

---

### Post by TehSofaWolf on 2011-09-28
As far as I know, you can't boot into an Ubuntu session through your BIOS.

---

### Post by mörgæs on 2011-09-28
Before going further I would recommend that you try a live boot from USB or CD. This will tell you how Ubuntu likes the hardware.

After this, it is not difficult to set up a dual boot with Vista.

---

### Post by wildmanne39 on 2011-09-28
Hi, you need to be careful when installing ubuntu that you do not by mistake over write your vista install, many people prefer to unplug there windows drive then install ubuntu then plug your windows drive back in then run this command in the terminal of ubuntu
```
sudo update-grub
``` 
that will give you the boot menu so you can choose which system you want to boot into.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

The advice to try it from the livecd is where you should start.
Thank you

---

### Post by audiomick on 2011-09-28
I don't think you need to be messing around with choosing in BIOS or anything like that. What you describe is a situation that can be easily covered with a normal dual boot installation. Read this:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

All you have to worry about during the install is to make sure you install to the empty disk. Go at it nice and slow, and really look at what is on the screen as you are going through the installation, and you will find it easy enough.

---

### Post by Gemius on 2011-10-07
Thank you all for your advice. I hope to get it working soon.

---

### Post by amjjawad on 2011-10-07
> **mörgæs said:**
> Before going further I would recommend that you try a live boot from USB or CD. This will tell you how Ubuntu likes the hardware.

After this, it is not difficult to set up a dual boot with Vista.

+1

Vista was the reason I moved to Linux :P

---

