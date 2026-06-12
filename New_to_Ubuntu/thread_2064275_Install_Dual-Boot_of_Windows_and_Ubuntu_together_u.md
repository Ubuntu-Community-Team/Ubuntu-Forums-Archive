---
title: "Install Dual-Boot of Windows and Ubuntu together using disk or usb (without WUBI ins)"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by CurseThePhobia on 2012-09-28
Hi there, i have download ubuntu 12.04 LTS and have burned it on a disk.I tried to install it to my loved Windows 7 PC ( i am LinDows User okay). I just wan to install it by dual boot it by installing from my ubuntu 12.04 LTS disk. Here are my question:

1. Do i can install dual boot it by disk?
2. Does it erase my current OS? (this is because it is not wubi installer. I guess~)
3. If it does keep my current OS (windows 7), does it erase all data, music, games and bla bla bla in my current hard disk?

Ok, that for today. I hope ya all help me. Thanks!:guitar:

---

### Post by newb85 on 2012-09-28
> **CurseThePhobia said:**
> Hi there, i have download ubuntu 12.04 LTS and have burned it on a disk.I tried to install it to my loved Windows 7 PC ( i am LinDows User okay). I just wan to install it by dual boot it by installing from my ubuntu 12.04 LTS disk. Here are my question:

1. Do i can install dual boot it by disk?
2. Does it erase my current OS? (this is because it is not wubi installer. I guess~)
3. If it does keep my current OS (windows 7), does it erase all data, music, games and bla bla bla in my current hard disk?

Ok, that for today. I hope ya all help me. Thanks!:guitar:

What you're asking is not only possible, it's quite common.  It's how I set this machine up.

1. Make sure you back up your important data.  Everything should go smoothly, and you shouldn't lose anything.  Back up anyways.

2. Defrag your Windows system.

3. Boot from the CD and run the installer.  It should give you an option to install alongside Windows.  Everything should be pretty self-explanatory.

4. Make sure both systems will boot normally.

5. Post your experience here...

---

### Post by oldfred on 2012-09-29
It can erase your entire system if you tell it to install to the entire drive, so do not choose that option.

How many partitions are used already?

Also best to test your system with LiveCD or USB to make sure everything seems to work well.

While in liveCD open a terminal and run this command to see what partitions you have. copy & paste or the -l is the small letter el not number 1 or letter I (eye). 

sudo parted -l

---

