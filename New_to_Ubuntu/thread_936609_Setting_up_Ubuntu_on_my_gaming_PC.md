---
title: "Setting up Ubuntu on my gaming PC?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by Grimhound on 2008-10-03
Alright, I really need you folks' help with this.

I've decided I want to try setting up Ubuntu on my desktop for the purpose of testing how Linux works as a gaming platform. Yet I'm still sort of a newbie to Linux.

Is there any easy way to set up a computer with the following to work for gaming purposes with Ubuntu, either with 8.04 or the 8.10 Beta?

-Intel Core Quad Q6600
-ATI Radeon HD 4850

---

### Post by Zzl1xndd on 2008-10-03
The Q6600 will work no problem out of the box, I have the same processor in my machine. I'm not sure about the ATI card though.

---

### Post by Paqman on 2008-10-03
The easiest way to install Ubuntu dual-boot is [Wubi](http://wubi-installer.org/). Just download and run the installer and it'll grab the right disk image and create a virtual hard drive to install Ubuntu onto.

However, downloading the LiveCD is useful, since it allows you to boot into a live session and check to see if your hardware is all supported. With the LiveCD you can either install the traditional way by partitioning your hard drive, or again you can boot back into Windows and launch Wubi from the disk.

Torrents are the best way to get the LiveCD ([Hardy download links](http://releases.ubuntu.com/8.04/)). I wouldn't recommend installing the Intrepid Beta if you're not familiar with Linux. There's at least one really gnarly bug on it right now.

What games were you thinking of running? Linux is good at a lot of things, but gaming isn't really one of them.

---

### Post by binbash on 2008-10-03
[http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1)

---

### Post by Grimhound on 2008-10-03
> **binbash said:**
> [http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1)

Figures. I buy a new video card and it has performance issues.

I really wish Linux gaming would get more support. I'd like to see it take over for Windows as the main gaming platform. :|

---

### Post by Paqman on 2008-10-03
> **Grimhound said:**
> Figures. I buy a new video card and it has performance issues.


It's all about the Nvidia cards for Linux. ATI support is pretty ropey, but is improving slowly.

> 
I really wish Linux gaming would get more support. I'd like to see it take over for Windows as the main gaming platform. :|

Me too, but i'm not holding my breath. I keep XP around solely for playing games on.

---

### Post by Grimhound on 2008-10-03
When I try to install the ATI Catalyst, I get the following error.
> Cannot install 'fglrx-amdcccle'

This application conflicts with other installed software. To install 'fglrx-amdcccle' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

Any ideas what's interrupting with it?

---

### Post by davidryder on 2008-10-03
I suggest trying Ubuntu in VirtualBox. It won't change anything with your boot records and is as easily uninstalled as deleting files.

---

### Post by Paqman on 2008-10-03
> **Grimhound said:**
> When I try to install the ATI Catalyst, I get the following error.

How are you trying to install this?

First place to go for graphics card drivers is always System > Admin > Hardware drivers. If you want a more bleeding-edge driver, try installing EnvyNG and use that to install your driver.

---

### Post by Grimhound on 2008-10-03
> **Paqman said:**
> How are you trying to install this?

First place to go for graphics card drivers is always System > Admin > Hardware drivers. If you want a more bleeding-edge driver, try installing EnvyNG and use that to install your driver.

It doesn't even detect the card. Or otherwise there's some issue with support of the motherboard. Currently I can't enable Compiz and I have no sound.

---

### Post by 3rdalbum on 2008-10-03
> **davidryder said:**
> I suggest trying Ubuntu in VirtualBox.

No, he can't do any 3D inside a Virtualbox guest.

---

### Post by binbash on 2008-10-03
> **Grimhound said:**
> When I try to install the ATI Catalyst, I get the following error.


Any ideas what's interrupting with it?

It conflicts with that package.YOu have to remove it.I strongly suggest install using envy-ng

---

