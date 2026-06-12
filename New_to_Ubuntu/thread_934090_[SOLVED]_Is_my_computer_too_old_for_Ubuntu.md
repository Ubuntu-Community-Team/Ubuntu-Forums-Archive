---
title: "[SOLVED] Is my computer too old for Ubuntu?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by paulo21 on 2008-09-30
I would like some expert information about the following query:

I am running Xubuntu, and later Ubuntu 8.04, on an Athlon XP 2600, 2Gb DDR and 300GB disk. I usually run Firefox and Deluge. I am a newbie on Ubuntu and Linux.

1- Why does Firefox eat so much CPU?

2- Why does Xorg end up with more than 40% CPU?

Is my computer too old for Ubuntu 8.04? I already switched to Xubuntu but the same problem happens when I run Firefox and Deluge at the same time.

Any help on how optmize this system or explanation about what is happening will be welcomed.

Thanks in advance.

---

### Post by hyper_ch on 2008-09-30
what video card have you got?

---

### Post by Odisej on 2008-09-30
Well, no, your computer is good enough to run Ubuntu without a problem. I just installed one on Pentium III, 400MHz, with about 512MB of RAM. It seems you have another problem at hand. Deluge shouldn't be a problem either. I think morei information about graphics would help. Are U using a desktop or laptop?

---

### Post by mister_pink on 2008-09-30
It certainly isn't too old, mine is very similar (Athlon XP 2400 instead) and it runs just great. Sounds like you're having some issues.

Ignoring what the numbers tell you, is it actually running sluggish? Sometimes the numbers can be misleading!

Also, do you have any of the desktop effects on?

---

### Post by rybaxs on 2008-09-30
1- Why does Firefox eat so much CPU?
I think you've open a site that eats much of CPU's process.. like Java or any J2EE development.. is this your first time using hardy? try to see if there is space available on your disk :D lol 300GB.. just guessing coz small free space sometimes lag up a system. try to off the desktop effects.. you specs is great!.. what brand is your motherboard?

---

### Post by paulo21 on 2008-10-04
I am using a GeForce 4400MX.

---

### Post by paulo21 on 2008-10-04
I am using a desktop.

---

### Post by paulo21 on 2008-10-04
> **mister_pink said:**
> It certainly isn't too old, mine is very similar (Athlon XP 2400 instead) and it runs just great. Sounds like you're having some issues.

Ignoring what the numbers tell you, is it actually running sluggish? Sometimes the numbers can be misleading!

Also, do you have any of the desktop effects on?
I switched to XFCE to have something lighter. I guess it is off. 

Where in XFCE can I switch it off?

---

### Post by paulo21 on 2008-10-04
> **rybaxs said:**
> 1- Why does Firefox eat so much CPU?
I think you've open a site that eats much of CPU's process.. like Java or any J2EE development.. is this your first time using hardy? try to see if there is space available on your disk :D lol 300GB.. just guessing coz small free space sometimes lag up a system. try to off the desktop effects.. you specs is great!.. what brand is your motherboard?
Yes, It is my first time using any flavor of linux. I chose Ubuntu because of the community, which anyone can have a problem solved and get information asap.

I using an ASUS A7V400-MX SE for Athlon socket A or 462. I have plenty od disk space, actually I have 2 disks: one where ubuntu is installed has 29.49 GB free space and the other one has 223Gb free space.

I switched to Ubuntu, primarilly to download files using bittorrent. After got fed up with Windows every 3 months nwe installation and management memory problems.

---

### Post by paulo21 on 2008-10-04
I am using conky as system monitor. It says Xorg is using CPU about 21% and Deluge other 20% average.

I would like to know how to tweak my system to get more performance.

---

### Post by JohnFH on 2008-10-04
With Xorg taking up a lot of CPU time, that almost definitely means the graphics card is not configured correctly.  Check that you are using the Nvidia restricted driver for it (System>Preferences>HardwareDrivers).

---

### Post by kansasnoob on 2008-10-04
As far as Firefox eating a lot of resources I've noticed that more and more web pages are loaded with small Flash crap. I've noticed my cpu usage is as much as 80% lower with flashblock installed.

It's in the repos so you can either install it from synaptic or:

```
sudo apt-get install flashblock
```

Then close and reopen Firefox. Those pesky unwanted Flash things are replaced by a F button you can click to play them.

---

### Post by bagle on 2008-10-04
if you still have problems with firefox try switching browsers to a more light weight one (eg. opera seamonkey):D:D:D:guitar:

---

### Post by paulo21 on 2008-10-05
> **JohnFH said:**
> With Xorg taking up a lot of CPU time, that almost definitely means the graphics card is not configured correctly.  Check that you are using the Nvidia restricted driver for it (System>Preferences>HardwareDrivers).
Yes, you were right. Yesterday I decided to clean re-install all my machine, and this time I did things right. The CPU consumption decreased and Xorg isn't eating that much cpu.

So, the problem was a misconfigurated video card.

Thanks you all.

---

### Post by paulo21 on 2008-10-05
> **JohnFH said:**
> With Xorg taking up a lot of CPU time, that almost definitely means the graphics card is not configured correctly.  Check that you are using the Nvidia restricted driver for it (System>Preferences>HardwareDrivers).
Yes, you were right. Yesterday I decided to clean re-install all my machine, and this time I did things right. The CPU consumption decreased and Xorg isn't eating that much cpu.

So, the problem was a misconfigurated video card.

Thanks you all.

---

### Post by carolinason on 2008-10-05
Not solved here.

Same problem with Firefox and Flash.

Video card is ATI Radeon 9000 using xorg 3d drivers.  I can run open arena great, but FF+Flash = 100% CPU and sometimes crippling the machine so much that I have to kill X.

I disabled desktop effects, but have to use Windows to see many web sites that run flash, where I haven't ever had to do this before.

Running flash block per a previous poster and this helps tremendously with the cpu, but i need to flash to work correctly, so i don't need to fire up the windows machine. i'm trying to save energy.

---

