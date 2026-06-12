---
title: "Wanting to download Ubuntu to Cd, but can only find instructions for DVD download"
date: 2016-04-21
forum: New to Ubuntu
---

### Post by lulu3 on 2016-04-21
I would like to make a CD with a newer version of Ubuntu. But there is only instructions for making a DVD or a USB download. Can I follow the DVD instructions and just substitute a CD in place of the DVD?:-k

---

### Post by vasa1 on 2016-04-21
Most of the recent Ubuntu's won't fit on a CD. That's why DVD or USB is the way to go.

---

### Post by Habitual on 2016-04-21
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by RobGoss on 2016-04-21
You would need a CD with more more the 700-MB

I always burn my ISO files on DVD'S with 4.7 GB this way you have more the enough space.

But as stated USB is another good way to install Ubuntu.

---

### Post by The Cog on 2016-04-21
To answer the original question: Yes, just substitute DVD for CD. The procedure is the same.

---

### Post by lulu3 on 2016-04-21
I'm guessing that it will not let me use multiple CDs. I have a new PNY USB flash drive with 8GB. I guess I'll try doing it that way. Before I do try the USB, I noticed on booting up, USB was not a choice on my PC. It has REMOVABLE -FLOPPY DISK,   HARD DISK - RD MASTER/ OR /   - BOOTABLE ADD-IN CARDS,   OR  CDROM. Will any of those let me boot from the USB? I'm thinking the answer is no, right? The computer is an old hand-me-down that I played with years ago and loaded Ubuntu 11.10 (I think) on it. The only other way to bring it up to a new enough version that is supported would be to update it one version at a time, correct? If I do it that way, does Ubuntu clear out the older files as it goes, or will my PC have to use a lot of space to fit the updates? 

  Oh, and by the way, THANKS SO MUCH TO ALL OF YOU AND YOUR HELP, GUYS!):P I'm sure by the questions I'm asking, you have already figured out I'm new at using Ubuntu!

---

### Post by howefield on 2016-04-21
Correct, you won't get Ubuntu on multiple CDs, the option REMOVABLE HARD DISK looks like your best bet.

If the computer is so old, you might be better listing the specifications before downloading something that might be a bit heavy for it.

---

### Post by LukeMorrison on 2016-04-21
You can use a helper application to boot from a USB drive, even if your BIOS does not support it.

[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

I have used this in the past with success.

---

### Post by vasa1 on 2016-04-21
> **lulu3 said:**
> ..., I noticed on booting up, USB was not a choice on my PC. It has REMOVABLE -FLOPPY DISK,   HARD DISK - RD MASTER/ OR /   - BOOTABLE ADD-IN CARDS,   OR  CDROM. Will any of those let me boot from the USB? I'm thinking the answer is no, right? The computer is an old hand-me-down ...
There's something called plop that lets you get around the lack of "boot from USB".

Take a look at
[https://www.youtube.com/watch?v=d7b4F6QJhVM](https://www.youtube.com/watch?v=d7b4F6QJhVM)
and
[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

I don't have first-hand experience with it.

---

### Post by lulu3 on 2016-04-21
So I'm guessing updating it 1 version at a time is a bad idea? I have the time to spare since my husband is out of town till tomorrow. Unless you think this way is not a good idea, or will take up too much space. Just curious if this way is possible.

---

### Post by Impavidus on 2016-04-21
Upgrading one step at a time (11.10&#8594;12.04LTS&#8594;14.04LTS&#8594;16.04LTS) is not really recommended. In principle it should work, the intermediate releases are still supported, but it will leave some dirt around. And it may take a very long time. You may not be ready for tomorrow, whenever that may be in your timezone. I've one computer upgraded 6.06LTS&#8594;8.04LTS&#8594;10.04LTS&#8594;12.04LTS&#8594;14.04LTS, but now I'm seriously considering a clean install of 16.04LTS because there are too many unexplainable problems now.

Given the age of your computer (you didn't give the full hardware specs), you may get a better experience using a lighter relative of Ubuntu. Consider Xubuntu or Lubuntu.

If you want to install from a cd, there is also the option to use a [minimal cd]("https://help.ubuntu.com/community/Installation/MinimalCD").

---

### Post by lulu3 on 2016-04-21
Well, I just went ahead and updated to the 14.04.4-desktop-i386.iso version.8-[ Like I said, I have plenty of time and it's a good thing! It says it will take 6 hours and 30 minutes. I'll let ya'll know the outcome when it gets done. Thanks for your help fellas!):P

---

### Post by lulu3 on 2016-04-21
I can't find my full hardware specs! Like I said I'm new to Ubuntu. If it was Windows I could have found my system info but all I found was the OS type was 32-bit and the Processor Intel Pentium 4CPU 2.80GHz x2 and Memory 432.08 MiB and Disk 78.3 GB. I'm not sure if those are what you meant by "specs". If this don't work then I'll try the USB boot suggestions from the earlier posts and do a clean install. The time is down to 4 hours and 40 minutes so it's going pretty fast so far. It's in God's hands now! [-o< Ha! Ha!

---

### Post by oldrocker99 on 2016-04-21
Hardware specs can be found out thus:```
lspci
lsusb
```.

---

### Post by oldrocker99 on 2016-04-21
> **lulu3 said:**
> I can't find my full hardware specs! Like I said I'm new to Ubuntu. If it was Windows I could have found my system info but all I found was the OS type was 32-bit and the Processor Intel Pentium 4CPU 2.80GHz x2 and Memory 432.08 MiB and Disk 78.3 GB. I'm not sure if those are what you meant by "specs". If this don't work then I'll try the USB boot suggestions from the earlier posts and do a clean install. The time is down to 4 hours and 40 minutes so it's going pretty fast so far. It's in God's hands now! [-o< Ha! Ha!

To find out specs:```
lspci
```.

I had a 32-bit 2006 Lenovo laptop which, before the keyboard died, ran Ubuntu MATE just fine. I'd advise Ubuntu MATE\\:D/, or Lubuntu or Xubuntu which work better on low-powered machines:wink:. 

Keep asking questions:confused:!

---

### Post by lulu3 on 2016-04-21
Thanks! I wrote them down to use when my upgrade is done. Thanks again, sir! :D

---

### Post by RobGoss on 2016-04-21
That depend on the individual and how much content and data you have

If your like me I can upgrade at any given time because I don't really collect a lot of files or data and I always have things backup

Sometimes it's not worth all the headache to upgrade from version to version, just go to the current one that's just me..

I went from 14.04 to 16.04 and all is good

---

### Post by UbuntuAddict99 on 2016-04-26
Hello Lulu3,

Yes, unfortunately Linux Ubuntu is just too large for the humble CD anymore DVD is the best way to go USB's are a hassle in my opinion, but honestly it makes no difference between a CD and a DVD to burn the ISO. And it is exactly the same way to burn it on either CD and or DVD just remember to verify the written data.

Happy Linuxing.

"Linux Ubuntu the final frontier!"
                                            -UbuntuAddict99

---

