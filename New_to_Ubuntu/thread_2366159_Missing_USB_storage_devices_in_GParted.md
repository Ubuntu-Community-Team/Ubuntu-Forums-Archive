---
title: "Missing USB storage devices in GParted"
date: 2017-07-14
forum: New to Ubuntu
---

### Post by Vaclav Vasek on 2017-07-14
I have updated to the latest Ubuntu and having some issues with detecting USB storage devices. 
I have been successfully  using a switch to alternate between my PC and Raspberry Pi controller, untill I have updated to the latest Ubuntu. 
I have EXTERNALLY powered D-link hub and that is where seems to be the problem. 

I can correctly identify  ALL connected USB devices to my PC using "lsusb" with appropriate option.  I can do same on Raspberry Pi Raspbian OS side. 

However, using GParted ( on Ubuntu) is a different story. It fails to identify multiple devices of same kind / vendor ( Lexar flash drives) either connected to my PC directly or connected via the D-link. 

Basically - I cannot use GParted any more and like to know why it showed up after updating to the latest OS and using SAME hardware - identical vendor  flash drives. 
 
As a relatively new user I am puzzled how simple working application - I assume GParted is just GUI front for lsusb command - can fail to work in new version of  OS. 
. 
I am not sure HOW to go back to previous version of Ubuntu.

---

### Post by oldos2er on 2017-07-14
Gparted is Gnome Partition Editor, it has nothing to do with lsusb.

To go to a previous version restore from backup, or if that's not a possibility you'll need to do a fresh install.

---

### Post by kurt18947 on 2017-07-14
It appears to me that GParted is broken on 16.04. I have lots of issues with an error message which right now I don't recall exactly; it's something about sector sizes. The version of GParted in 14.04 works fine. I'm using Ubuntu-Gnome if that matters.

---

### Post by Vaclav Vasek on 2017-07-15
At this point I just cannot put the blame squared on GParted. 
Been playing around with lsusb and D_link hub and found out that when I DO NOT POWER the D_link externally the lsusb can detect up to four identical flash drives (200 mA each) BUT only on boot. 
It looks as removing / inserting these drives during run time is just ignored. 
USB monitors the power connection and should detect the device insertion and in case of these drives - the  LED should light up. It does not - at run time!
So- maybe the D-link connection to external power source  is caput?
It does read over 5 V at idle and I have no real means to read it after it is running without taking the box apart. 
( I may sacrifice / cut USB cable so I can read the bus that way) 

What would be nice is to get real power reading on USB via software.

---

