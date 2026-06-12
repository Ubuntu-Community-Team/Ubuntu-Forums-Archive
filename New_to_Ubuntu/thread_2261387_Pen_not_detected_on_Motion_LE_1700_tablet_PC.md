---
title: "Pen not detected on Motion LE 1700 tablet PC"
date: 2015-01-18
forum: New to Ubuntu
---

### Post by lonrot on 2015-01-18
Hi,

I installed Lubuntu-14.10-desktop-i386 on a Motion LE 1700 tablet.

The pen is still unrecognized after running automatic updates.

How can I solve this?

---

### Post by lonrot on 2015-01-19
Also the device is not detected in the xinput list:

> &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:101b	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:4024	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:400e	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard   

---

### Post by lonrot on 2015-01-22
I can't find step by step instructions to install [Linux Wacom Tablet drivers]("http://sourceforge.net/projects/linuxwacom/") on Lubuntu 14 (32 bit).

I'm unable to succeed with Ubuntu instructions.

The installation fails somewhere down the road.

Can someone share this?

---

### Post by sandyd on 2015-01-23
Hi, what wacom tablet are you trying to install drivers for?

---

### Post by vasa1 on 2015-01-23
Hmmm ....
[http://askubuntu.com/questions/577171/what-im-doing-wrong-with-wacom-drivers](http://askubuntu.com/questions/577171/what-im-doing-wrong-with-wacom-drivers)

---

### Post by lonrot on 2015-01-24
> Serial Wacom Tablet stylus and > Serial Wacom Tablet eraser [should appear in the xinput list]("http://ubuntuforums.org/showthread.php?t=2217121") on a [Motion LE 1700 Tablet PC]("http://www.pcworld.com/product/1372076/motion-le1700-tablet-pc.html"), however they are missing in Lubuntu 14 (32bit).

Is there a way to make Lubuntu discover these devices?

**Note:** Linux Mint and Elementary OS recognize these devices right out the box.

---

### Post by lonrot on 2015-01-24
> **sandyd said:**
> Hi, what wacom tablet are you trying to install drivers for?

It's a Motion LE 1700 Tablet PC. After several hours of research, I noticed that everyone who's got the same Tablet and Lubuntu can use the stylus right away. Other distros have worked perfectly fine for me, even the BIOS menu manages to read the pen gestures, only Lubuntu has issues.

I will download a new DVD version of Lubuntu and see if it works.

---

### Post by lonrot on 2015-01-24
I just tried with a fresh Lubuntu 14.04 Live CD and it didn't detect the stylus. Looks like this an issue with newer releases and the support for this Tablet PC has been dropped by Lubuntu.

---

### Post by mörgæs on 2015-01-25
Please keep all your questions regarding a topic in the same thread. 
I have merged twice.

---

### Post by lonrot on 2015-01-25
> **mörgæs said:**
> Please keep all your questions regarding a topic in the same thread. 
I have merged twice.

They are similar questions but not the same.

One question is about driver installation and the other is about device detection in Lubuntu.

---

### Post by lonrot on 2015-01-25
I was able to get the Stylus back by duplicating the steps posted [in this answer]("http://askubuntu.com/questions/541505/thinkpad-x41-tablet-wacom-stylus-stopped-working-on-lubuntu-14-10").

I still have no idea how to update wacom drivers properly, but the stylus works perfectly fine for the time being.

---

