---
title: "Totally new on ubuntu"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by gunner5 on 2016-04-23
Hello guys, i was some kind of reticent to change to ubuntu but now im in love with it.
Using 16.04 lts now and im really happy, but some minor issues are troubling me; for example, the temperatures are a little high than windows, and i have readed maybe is for drivers, so i want to confirm it. A couple of days ago i was testing mint rebecca and the same issue but when wifi is running, doing a connection via ethernet it was less warmer.
Thx in advance.
PS: hp 14-d036la is my laptop.

---

### Post by RobGoss on 2016-04-23
Hello Gunner welcome to the forum,

I have always found Laptops to get a bit hotter them any other machine, I have always use a cooling plate to keep mine laptop from over heating and for the most part it works great. To tell you the true I never pay to much attention to over heating because I have a number of fans on my desktop to help with these issues.

---

### Post by grahammechanical on 2016-04-23
There is a utility in Ubuntu Software called Psensor. That will put an icon in the top panel & it has a drop down menu that shows all kinds of temperatures as well as fan speeds. CPU, Motherboard, GPU, hard disks. You can keep an eye on what is actually happening.

Regards

---

### Post by RobGoss on 2016-04-23
> **grahammechanical said:**
> There is a utility in Ubuntu Software called Psensor. That will put an icon in the top panel & it has a drop down menu that shows all kinds of temperatures as well as fan speeds. CPU, Motherboard, GPU, hard disks. You can keep an eye on what is actually happening.

Regards

That's a nice little app G, thanks for posting it

---

### Post by $yl9pAR%t on 2016-04-23
Did you install proprietary driver for your GPU? Open terminal and give us the output of:

```
inxi -b
```

---

### Post by gunner5 on 2016-04-23
Thx for all support guys, i remember now when i disabled the nvidia card wasnt that hot but that was on mint rebecca. And i had a big problem with nvidia driver, my previous mint got totally ruined... lol
And for that i was a little reticent for doing it. How can i know about what driver is more stable for me? Im with a 820m.

```
gunner@gunner-ubuntu-PC:~$ inxi -bSystem:    Host: gunner-ubuntu-PC Kernel: 4.4.0-21-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Hewlett-Packard product: HP 14 Notebook PC v: 0976100000405F10000610180
           Mobo: Hewlett-Packard model: 21BB v: 39.15
           Bios: Insyde v: F.11 date: 03/21/2014
CPU:       Dual core Intel Core i5-3230M (-HT-MCP-) speed/max: 1200/3200 MHz
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
           Card-2: NVIDIA GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M]
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile
           GLX Version: 3.0 Mesa 11.2.0
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           Card-2: Realtek RTL8188EE Wireless Network Adapter
           driver: rtl8188ee
Drives:    HDD Total Size: 500.1GB (1.5% used)
Info:      Processes: 224 Uptime: 11 min Memory: 1083.9/3843.8MB
           Client: Shell (bash) inxi: 2.2.35 
```

---

### Post by $yl9pAR%t on 2016-04-24
If you had only nvidia graphic card I would say you should install proprietary nvidia driver to lower CPU usage (and hopefully temperature), but I see you are using intel card and I do not know how impact it can have on temperature, switching from intel to nvidia card.

Anyway you would expect to gain better performance at least.

---

### Post by gunner5 on 2016-04-24
Yep, xorg thing on mint allowed me to change intel graphics for performance. I will try it and tello you guys how it was it.
Thx again.

---

