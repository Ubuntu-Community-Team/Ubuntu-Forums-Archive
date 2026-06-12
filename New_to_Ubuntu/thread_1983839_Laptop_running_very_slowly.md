---
title: "Laptop running very slowly"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by Loki57701 on 2012-05-20
Before I pose my question I'm going to post my system specs and OS info.

OS:         Ubuntu 12.04 w/ Cinnamon 
Laptop
CPU:        Intel core 2 duo 2.53Ghz
Memory:     4Gb
Video Card: Nvidia GeForce 9800M GS 512Mb
HDD:        Western Digital 7200rpm 320Gb

----------------------------------------------------

It's not a 'top of the line' machine, but it's not bad.

I've run several different distributions of Linux on this laptop and I've never noticed any problems, but with 12.04 it seems.. slow. I know that's very broad, but it's quite noticeable. There is a discernible lag when logging in, opening applications, or doing anything even remotely CPU intensive.

I've checked my logs for errors and I even installed a command line utility called 'sensor' which shows your cpu temp. I was thinking maybe my system was overheating, but everything seems fine. 

I'm not running VM's, hosting a website, rending 3d animations.. nothing that should really slow the system down. When I check top my cpu is mostly idle, and I have plenty of free memory, so I'm not sure where to look.

Oh, and I have all the latest updates.

I would appreciate any ideas.

---

### Post by wilee-nilee on 2012-05-20
you run the lm-sensor load?

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Can't say really what the problem might be other then there are lags on getting to the desktop really to on my set up, once there runs pretty fast, older dual core with 2 gigs ram.

---

### Post by Loki57701 on 2012-05-20
I did run lm-sensor and I found no problems.

Oddly enough I switched back to unity and everything seems to work much faster, or more like normal I should say. I was under the impression that cinnamon was a bit lighter on resources than unity, but maybe I'm mistaken. 

Anyways, thank you for the suggestion. I'm going to mark this as solved for now.

---

