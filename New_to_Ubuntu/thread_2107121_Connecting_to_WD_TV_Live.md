---
title: "Connecting to WD TV Live"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by pedropumpalot on 2013-01-21
Hi all,

I've trawled the forums to find an answer for my question but I am none the wiser after a few hours looking.

I have a WD TV Live which is wired directly into my wireless cable router. 

I am using Ubuntu 12.10 on my laptop and I connect wirelessly to the internet. 

Below is a screenshot of the arp -n from my laptop:

Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.3                      (incomplete)                              wlan0
192.168.0.4              ether   d0:e5:4d:bc:d5:3d   C                     wlan0
192.168.0.1              ether   c4:3d:c7:44:f6:d0   C                     wlan0
192.168.0.8                      (incomplete)                              wlan0
192.168.0.5                      (incomplete)                              wlan0
192.168.0.2              ether   90:21:55:b2:c9:9f   C                     wlan0
192.168.0.6              ether   00:23:4d:82:f2:25   C                     wlan0


Can anyone tell me how I can share files from my laptop over the Wifi onto my WD Tv Live? 

I hope someone can help.

Cheers,

Pedro

---

### Post by Cheesemill on 2013-01-21
You need to set up Samba on your laptop to share the required folders.

Just right-click on the folder you want to share and select Properties > Sharing and then tick the required boxes.

When this is done you can use the menus on the WD Live to point it to your shared folder.

---

