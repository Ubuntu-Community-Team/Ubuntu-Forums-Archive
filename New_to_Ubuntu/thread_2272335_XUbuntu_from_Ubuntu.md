---
title: "XUbuntu from Ubuntu"
date: 2015-04-05
forum: New to Ubuntu
---

### Post by Mark_McDonald on 2015-04-05
I downloaded and saved the torrent file of Xubuntu to a USB, went into BIOS to make USB 1st at bootup. 
Nothing happened, it just proceeded to go to the usual Ubuntu layout as before.
I do remember installing my original Ubuntu via USB.
Will I have to reformat my laptops HD?

I can press an F key and get to this........a screen called "GNU BRUB version 2.02~beta2-9ubuntu1"

I got everything I need on my external HD which is unconnected now. My original Ubuntu was installed to internal laptop HD.

Edit, I realize now I need a ISO to USB program, which I searched on cnet.com and got. Just a hickup is all. I believe I am on the right track, the Ubuntu website confirms this and I only had one ISO file, which they said is incorrect file. I need more then the one file, I need the ISO file unzipped or whatever onto my USB drive. Then boot from USB. Progress my Linux friends, progress not perfection. So ya now I am going through the process now. Its awesome to have a up and running desktop to search from.
Solved my own problem.

Tell me why if I am installing XUbuntu, why the setup is saying Ubuntu?
Another question is, I am installing Ubuntu 14.04.2 LTS, I am confused on the different updates, because I had a choice of 2. The 14.10 LTS and 14.04.2LTS, I originally installed Ubuntu 14.10LTS, but now I went to XUbuntu, so going towards same question as mentioned previous ^^^^^^^^^^^^

I installed the ISO from XUbuntu, exactly the same layout on computer as my original Ubutnu. I can only assume nothing has changed, except I have a freshly installed 64bit Ununtu 14.04 LTS.

---

### Post by flaymond on 2015-04-06
Xubuntu is Ubuntu actually, it's just different desktop enviroment and softwares installed. Xubuntu use Ubuntu system as the base, that's why it appears as ubuntu. You can install 14.04.1 or 14.04.2, but recommend to download the latest. For your installation problem, you cannot just download the file and put it in the USB just like that. You need to make the USB bootable and a program to install the ISO into the USB.
Actually, UnetBootIn software make this easier for a beginner to install Linux.

Tips after installing Ubuntu, Xubuntu or whatever you may install is firstly, do a 'sudo apt-get update && sudo apt-get upgrade'.

By the way, it's Xubuntu, not XUbuntu. However, it depends on your choice to call it as what. :D

---

### Post by newb85 on 2015-04-06
14.10 is not LTS.  14.04 (and all it's point releases, including 14.04.2) is not LTS.  What that means is that 14.04 is supported for five years from release date (April '14 - April '19), and 14.10 is supported nine months from release date (October '14 - June '15).  Running a release that is no longer supported is very bad practice from a security standpoint.  I highly recommend you go with 14.04.2.

---

### Post by flaymond on 2015-04-06
Yup, totally agreed with newb85. LTS is better because it been released for stable version, while 14.10 Utopic Unicorn is somehow buggy ( I gonna list it for testing purpose because it's for 9 months support while LTS give you 5 years support and 14.04 support probably will end in April 2019)

---

### Post by Mark_McDonald on 2015-04-08
OK got it, thanks everyone. I have a good freshly installed Xubuntu 14.04.2 LTS (from command liine 'lsb_release -a'), and it works perfectly. I am loving it!
I thought I updated everything through the desktop, but I did the terminal updates and upgrades anyway.
Thanks for the help!

---

