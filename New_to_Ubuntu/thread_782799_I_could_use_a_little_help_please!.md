---
title: "I could use a little help please!"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by redpete on 2008-05-05
I downloaded Hardy a few days ago and have more than a few questions! Right now I have a dual boot with Win XP.

Perhaps the most pressing is to get my WiFi working. it wont even switch on but it's fine under XP though so I presume it's a driver issue. I tried: [http://ubuntuforums.org/showthread.p...swrapper+howto](http://ubuntuforums.org/showthread.p...swrapper+howto)
but problem is there's no driver listed under hardware.

So where do I get one from and how do I install it? 


Thanks Pete

Hardy 8.04
PC Compaq presario M2000
Wifi card: Broadcom BCM9 4318 (rev4)

---

### Post by phr0ze on 2008-05-05
This thread was written for you.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

How To: Broadcom 4318 in Hardy.

Good luck

---

### Post by redpete on 2008-05-05
Hi,

Yes I've seen that. The problem is that if I go where the instructions (at top of page) under Hardy tell me to, i.e.
System/Admin/Hardware Drivers it's not there.

So should I try the Native bcm43xx driver: listed under Feisty/Gutsy or is there something newer? 
 
The thread seems to imply it must easier under Hardy and the drivers already there. So I'm wondering if it's on the CD I downloaded but did not instal? :confused:

---

### Post by ilrudie on 2008-05-05
I had a similar problem when upgrading from Gutsy to Hardy on an old dell m600.  Hardy recognized that it needed a restricted driver but with out wifi I had to use a wired connection to download the required packages.  Once I plugged in it installed the necessary packages and imported all my old wifi settings just fine.

---

### Post by redpete on 2008-05-05
I can download it in windows if need be. I just need to know what to download and where to install it! But the tutorial seems to imply it shouls already be there?
Pete

---

### Post by ilrudie on 2008-05-05
I think you are trying to make it harder then it is.  Try using a wired connection.  With my driver Ubuntu had to connect to the internet to get the files it needed but it did it automatically once I plugged in.

---

### Post by Moop on 2008-05-05
> **redpete said:**
> I can download it in windows if need be. I just need to know what to download and where to install it! But the tutorial seems to imply it shouls already be there?
Pete

When they imply that it's already there, they usually mean that it's in the repositories and available to download with a internet connection. You can use the cd as a source by going to System-Administration-Software Sources and checking the box for cd. Maybe the driver you need is on it, wouldn't hurt to check. 

You can download packages you need from here [http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/) but it can be pretty complicated when packages have multiple dependencies. Finding a wired connection you can use is the way to go.

---

### Post by pmaconi on 2008-05-05
Follow the directions here: [HowTo]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff"). I had the same problem as you (it wasn't showing up in hardware devices).

---

