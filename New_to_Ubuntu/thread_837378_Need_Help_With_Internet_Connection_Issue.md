---
title: "Need Help With Internet Connection Issue"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Mastamind1020 on 2008-06-22
Ok, so after years of having Windows XP i've changed my desktop to Ubuntu 8.04 (Hardy Heron). I've connected/reconnected my desktop to the router I've been using which is also connected to an Xbox 360 and a laptop running Windows XP SP2. 

After I first loaded Ubuntu I was able to download the most recent updates and go online an everything. After I turned off my computer for the first time my screen resolution went down to 800x600, I should also mention that I'm using an Nvidia Graphics card, after looking at the various forums on here I was able to kind of fix this problem after going into Terminal and doing the sudo xserver fix but right after I did that, my internet connection stopped working. I've tried everything I could think of to fix this and nothing has worked, but my Xbox and laptop (what I'm typing on now) is able to connect to the internet with no problem..is there anyone that can help me?

As I mentioned, everything was working fine until I went into Terminal and did the sudo xserver thing but I should also note that the same thing happened to me while using Xubuntu but I think it was just a firewall thing.


PPPLLEEAAASSSEEE HHHEEELLLPP

---

### Post by Zenze on 2008-06-22
Ok well I am guessing that the reason for your video problem has something to do with the updates, a kernel update messed up my video driver settings a few times. I would recommend going here for all your nvidia video driver needs, its very straightforward and easy to follow: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

As for your internet Im not really sure, as Im pretty new to ubuntu/linux as well. First guess though would be to make sure that its set to use dhcp and assign you an ip address automatically versus using a static ip. Just click the newtork icon in the top right and click manual config. Then just select your connection and enable roaming mode.

---

### Post by Mastamind1020 on 2008-06-22
Thanks Zenze for the help about the video card, as far as my internet connection goes, i've had the Roaming mode enabled since I installed Ubuntu but my only concern was that the box to the left of it was a "dash" rather then a check mark...does that make any difference? In any event, I'm still not able to connect to the internet

---

### Post by cariboo on 2008-06-22
Yes it does make a difference, if you put a check in the box your network access should work again.

Jim

---

### Post by Mastamind1020 on 2008-06-22
cariboo907, I've been trying to change that dash into a check mark in the Wired Connection box but it seems the only way I can do that is by going into the Wired Connection properties and unchecking the Roaming Mode box and choosing one of the other configuration settings, and still nothing has worked. 

Since I'm connection through a router, only the Wired Connection should have a check mark beside it right?..or should the Point to Point connection have a check as well because right not both still have only dashes.

---

