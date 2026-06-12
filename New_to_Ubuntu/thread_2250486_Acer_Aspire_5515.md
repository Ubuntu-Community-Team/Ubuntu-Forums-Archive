---
title: "Acer Aspire 5515"
date: 2014-10-28
forum: New to Ubuntu
---

### Post by Benjamin5th on 2014-10-28
I still consider myself a "noob" at linux, although I have installed and made LiveCD's many,many,many times. So I was baffled when I tried to install Ubuntu (Along with Zorin, Xubuntu, Lubuntu, Puppylinux, etc) on a laptop that was gifted to me.

The laptop is a Acer Aspire 5515, It originally ran (And I guess still does run) Windows Vista. It has a AMD Athlon Processor (model 2650e) And from what I've Googled, 1GB of ram.

I, for the life of me, cannot get any version of linux to install/boot from a CD/DVD.

I went into the BIOS settings and made sure it would try to boot from the CD-ROM first. 

No luck.

I thought is was the fact that it is a AMD processor, where most of my other computers have had Intel Processors. But again, I consider myself a noob so I am asking the great and mighty Linux excepts. [-o<

Last thing you should know, the laptop was given to me because the original owners forgot their password, and have no way of recovering them. So I can't access Windows.

Hope you guys know what to do!

(preferably, I'd like to be able to access the hard drive and recover the original owners files to give back to them. But if worst comes to worst I guess I'm good with wiping it)

---

### Post by yancek on 2014-10-28
> I thought is was the fact that it is a AMD processor,

Definitely not that.  I have an AMD processor and about a dozen Linux distributions installed.  If you have the boot priority set correctly and can't even boot, I would expect hardware problems, either loose connections or bad drive.

---

### Post by Benjamin5th on 2014-10-28
> **yancek said:**
>  If you have the boot priority set correctly and can't even boot, I would expect hardware problems, either loose connections or bad drive.

I can tell it tries to read the disk. The screen goes black and I see the white blinking "cursor" in the top left corner while the disk drive buzzes. But then it seems to give up and boot into windows after 15 or so seconds.

---

### Post by amanchesterman on 2014-10-29
It might be that the disk drive is faulty then. Try installing Linux from a Live USB stick -- I use that every time these days.

---

### Post by Impavidus on 2014-10-29
Most computers sold in the past 8 years support booting from usb. That includes most computers sold with Win Vista preinstalled. Have you tried booting from the live dvd on a different computer? It may tell you whether the dvd is good or not. You may have used several, but if the computer doing the burning does a bad job... Have you paid attention to the difference between 32 and 64 bit systems? Most computers of the past 8 years support 64 bit, although with just 1GB of memory 32 bit may be better. Ubuntu may not work if you have insufficient ram, but if it runs Vista, it should be able to run about any Linux version. You can check the ram and other specs from the bios menu.

Creating a live usb:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
If one method doesn't work, try one of the others. Recently I had no success using usb-creator, but mkusb worked.

---

### Post by mastablasta on 2014-10-29
linuxliveUSB (windows poragm), unetbooting, Yumi - will create bootable USB drives just fine. 

many things could have gone wrong. we need to get the computer to boot Linux first and then we can explore further.

also there are tools that will recover windows password. you could also just reset it. it's just a user password...:
e.g. [http://www.wikihow.com/Reset-a-Windows-XP-or-Vista-Password](http://www.wikihow.com/Reset-a-Windows-XP-or-Vista-Password)

---

### Post by Penguin360 on 2014-10-29
As suggested above, make sure the DVD drive is not faulty. If the DVD drive is good, then make sure you use the lower burn speed to make the installation DVD disk, for example 4X instead of the maximum speed.

If the internal DVD drive is bad, then you can try Live USB drive to boot, or you can use an external USB DVD drive to boot if you have one.

---

### Post by Benjamin5th on 2014-10-30
I have used the disk on computers both newer and older, so I know it's not the disk. 

I'll try a LiveUSB, What distribution would you all recommend? I am thinking Xubuntu, but if there is something better, lets do it :p

Also, would a newer version (I'm going to use Ubuntu for the sake of it) be bad? For instance, would it be better to use Ubuntu 10 or 12 instead of 14 since it's an older computer, and may not be compatible with newer versions?

---

### Post by mörgæs on 2014-10-30
Always newest release. At least 14.04.1, maybe 14.10 if you can live with the short term support.

---

### Post by Benjamin5th on 2014-10-30
> **mörgæs said:**
> Always newest release. At least 14.04.1, maybe 14.10 if you can live with the short term support.

So there won't be some form of incompatibility of the newer software interacting with older computers? (Great news! :p)

---

### Post by mörgæs on 2014-10-30
There are always exceptions but they are few. Please go experiment with 14.* and post your findings.

---

### Post by Benjamin5th on 2014-10-30
> **mörgæs said:**
> There are always exceptions but they are few. Please go experiment with 14.* and post your findings.

I'll be sure to do that :)

Thanks everyone for the input!

---

### Post by Benjamin5th on 2014-10-31
Unfortunately the USB did not work. I installed Xubuntu 14.04 on it.  In the BIOS, I have the boot order as:

USB CD/DVD ROM
IDE0: WDC WD1600BEVT ( it goes longer, but I don't think the rest of the numbers mean anything to you guys)
IDE1: TSSTcorp CDDVDW (Etc)
Network Boot: Realtek boot agent
USB FDD:
USB HDD:
USB KEY

I also tried setting USB HDD and USB KEY first, just to try. They didn't work either.

I'm lost as to what I did wrong. The iso appeared to install smoothly onto the USB.

---

### Post by mörgæs on 2014-10-31
IDE0 is the hard disk and IDE1 is the DVD drive. You need to move IDE0 and Network to the bottom, IDE1 to the top.

---

### Post by Benjamin5th on 2014-10-31
> **mörgæs said:**
> IDE0 is the hard disk and IDE1 is the DVD drive. You need to move IDE0 and Network to the bottom, IDE1 to the top.


Wow, I feel so stupid...*facepalm*

Works like a pro now! :) Obviously I have a long way to go before becoming a Linux guru.;)

Thanks so much for your help! This is one of the most responsive forums I've ever visited, I really appreciate you and the others who help people like me out.

---

### Post by mörgæs on 2014-10-31
Welcome to the free world.
Please mark the thread 'solved'.

---

