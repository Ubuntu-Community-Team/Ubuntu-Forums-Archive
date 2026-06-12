---
title: "Movies don't play well"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-04-08
Bs'd

Some movies give me trouble when playing them in movie player or VLC media player. 

They stop for a second, and then jump forward, stop again, en sometimes the picture gets all messed up, usually when the picture is moving fast.

I'm having an old PC, with 10.04 LTS version of Ubuntu on it.  It's 3 Ghz, one Gig RAM.  

What can I do about that?

---

### Post by TeoBigusGeekus on 2012-04-08
What's your video card?

---

### Post by Carnivorum on 2012-04-08
> **TeoBigusGeekus said:**
> What's your video card?

Bs'd

I have no idea, how can I find out?

---

### Post by ajgreeny on 2012-04-08
Use command ```
lspci
``` or ```
sudo lshw -C display
```

---

### Post by Carnivorum on 2012-04-08
Bs'd

This is what I get: 

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:09.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by d4m1r on 2012-04-08
Did you recently start running into this but it was working previously? What kind of videos are you trying to play?

If you are tying to watch 720p/1080p videos with 1GB of RAM and an integrated video card (like yours), I would not be surprised if it *is* choppy. I'd recommend upgrading your video first, and your RAM as well.

---

### Post by Carnivorum on 2012-04-29
> **d4m1r said:**
> Did you recently start running into this but it was working previously? What kind of videos are you trying to play?

If you are tying to watch 720p/1080p videos with 1GB of RAM and an integrated video card (like yours), I would not be surprised if it *is* choppy. I'd recommend upgrading your video first, and your RAM as well.

Bs'd

I'm playing movies of 700-800 Mb.

I just upgraded my RAM from 192 Mb to 1 Gb.  I'm on an old comp, but older comps with even less RAM play movies without a hitch.

---

