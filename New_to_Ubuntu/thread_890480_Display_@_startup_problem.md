---
title: "Display @ startup problem"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by SnapCount on 2008-08-15
Hi guys, I have finally decided to install and run ubuntu on my pc and see what everyone is talking about:). But I need some help. Ive been reading a magazine article for beginers of ubuntu. It said that you should install EnvyNG and update the to the latest graphics drivers, which I did. 

Everything seemed fine until I was exploring the different apps in the system menu, and saw that in the “Hardware Drivers” that the driver was not inuse, eventho I was able to run “Extra” visual effects. So I enabled the option in Hardware Drivers and restarted the PC. But now everytime the logon screen appears, it seems to be croped and I no longer have the option to select the option button in the bottom left hand corner and the power button I think in the bottom right hand corner:(.

Can someone please help me? I really dont want to reinstall ubuntu and download another 200+mb worth of updates if I can.

---

### Post by Crafty Kisses on 2008-08-15
You can reconfigure X by doing the following
```
sudo dpkg-reconfigure xserver-xorg
```
From there it will pretty much restore X, then try again.

---

### Post by SnapCount on 2008-08-15
Yep that did the trick :) Thanks for that. This is one hell of a big world im gona have to learn ;)

---

### Post by Tom--d on 2008-08-15
> **Codename said:**
> You can reconfigure X by doing the following
```
sudo dpkg-reconfigure xserver-xorg
```
From there it will pretty much restore X, then try again.

Yeah, That always works when my X screws up ;)

---

