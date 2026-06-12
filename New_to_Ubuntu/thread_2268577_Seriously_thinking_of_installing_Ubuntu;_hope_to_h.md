---
title: "Seriously thinking of installing Ubuntu; hope to have some questions answered."
date: 2015-03-09
forum: New to Ubuntu
---

### Post by anthony54 on 2015-03-09
Evening all,

I have been using OpenSuSE since version 7 (many moons ago).  Honestly I am a little more than burned out on it, thought I would give Ubuntu a try. I downloaded the iso and ran it in a virtual machine, runs fairly well, and just for laughs I thought "lets see what happens when I tell Ubuntu to find my wirelss printer", well it found it.  Funny thing is under opensuse I have to get the drivers from the manufacturer and manually install them.  So that got me thinking: maybe it is easier (as I often hear) to use, and more compatible with my hardware.  I am a long time linux user so yes I am aware that not all hardware is compatible, so tweaking is not an issue, I just would have to get use to the way things are done on an Ubuntu system.

Questions I have first:

1 - How customizable is the Unity desktop? As in, if anyone has used the KDE DE you understand it is highly customizable. If it is not, what about the Gnome 3 DE?  I understand that there is quite a bit of heartburn from some people about these DE's, but I actually find them a little refreshing. I also understand that I can install the KDE DE alongside of either of these (as I already did under the VM).  So if need be, I can always use KDE.

2 - I have an ATI/AMD HD 6450 video, which works fairly well.  Under opensuse I use the radeon driver as I have had issues with the fglrx driver working one minute, breaking my system the next.  I noticed that AMD actually has an "Ubuntu" driver, so my question would be: does the fglrx driver install fairly easy under Ubuntu? or is it the same with the on/off working (breaking) of the system.

3 - If there are other former opensuse users out there, was the transition easy enough? I ask this referring back to a previous point of the system being configurable to my liking.  I like to be in control of the system, if I didn't I would be using another proprietary system such as windows or mac.

Any and all wisdom is much appreciated, thanks in advance!

---

### Post by grahammechanical on 2015-03-09
I use Ubuntu with Unity and I consider myself in control of my system. I do next to no modification of the user interface. It is enough for me that the OS is stable and I can get on and do work with it. From the beginning Ubuntu was meant to be easy to use. And it is that. And as far as I can tell part of the reason for Ubuntu's ease of use is the lack of extensive customisation opportunities. We can set up certain fancy effects using the Compiz Configuration Settings Manager (CCSM) and other available tweak tools. But those tools give us the power to break the desktop.

Kubuntu (KDE) on the other hand has customisation built in. You might prefer that. It is better to install either Kubuntu, Xubuntu, Lubuntu, Ubuntu Gnome or Ubuuntu Mate than install a different desktop environment onto Ubuntu. You can do that if you wish, But I would not.

Ubuntu runs on Gnome 3 DE. It has the Unity UI instead of the Gnome 3 shell UI. The two UIs work on similar principles. Gnome organisation provides extensions to the UI as a way of customisation.

Ubuntu and its flavours have an Additional Drivers utility that will install proprietary video drivers for us. We usually get an offer of 4 variants of stable proprietary video drivers as well as the facility to use the open source video driver that is default in Ubuntu. Things break when we install newer proprietary video drivers that we download from a web site. Hybrid graphics present issues with any Linux distribution. And like other Linux distributions Ubuntu is dependent on the work of open source developers or proprietary developers.

Regards.

---

### Post by anthony54 on 2015-03-09
Thank you for the insight grahammechanical.  I am familiar with compiz, have used that since the beryl days.  Not sure if I asked the video driver question correctly; with opensuse after installing the proprietary driver (even one provided by opensuse) my system usually does not want to start the graphical interface unless I spend hours tweaking it. Only to have it break again after updates to the system.  This is what I wish to avoid.

I knew I would forget a question:

4 - as I already have opensuse installed, and am happy with the way the partitions are setup, would I be able to inform *buntu to use the existing partitioning without alterations (other than formatting)?

---

### Post by maestrobwh1 on 2015-03-09
Firstly, I have tried Debian, Arch, and even Suse.  I always come back to Ubuntu/Kubuntu due to the "just works" and "looks great" factor/  Arch always killed me at some point on dependencies and always having to build thing from AUR. This does not mean Ubuntu has been flawless since 2006, I've had either wifi or video issues in the past but honestly, that was a while ago so unless you have some new fangled hardware, there is high probability that everything should run smoothly, including installing in your current partition scheme.

---

### Post by anthony54 on 2015-03-09
Thanks for the input maestrobwh1, I think I will just take the plunge. After all, worse case scenario I have to change it back.

---

### Post by Bucky Ball on 2015-03-09
I prefer xfce4 desktop environment myself. Highly configurable.

Welcome and enjoy the learning curve. ;)

---

### Post by anthony54 on 2015-03-09
Thanks much Bucky Ball; as previously stated the learning curve will be learning how things are done in *buntu.  A feature that I liked with opensuse (some did not) is the yast control center, everything in one place, I hope to find something similar.

---

### Post by sammiev on 2015-03-09
I have a very good liking for OpenSuSE but my main OS is Ubuntu-gnome. I use VMware to play with all the rest and usually have 2 - 4 OS installed within a VM.

It's about choices and if you have time to play. :)

---

### Post by anthony54 on 2015-03-09
Appreciated sammiev.

---

### Post by anthony54 on 2015-03-09
Reporting back from within Ubuntu now.  All went well enough, just installed the ATI binary from the software center, rebooted and all seems fine.  Curious though as to where I might find the ATI "CCC" comand and control center?  If anyone would be so kind as to help it would be greatly appreciated.

---

### Post by Bucky Ball on 2015-03-09
Look for fglrx-amdcccle in Software Centre.

---

### Post by mattharris4 on 2015-03-09
Welcome to Ubuntu!  I actually use Edubuntu on my office computer as it has several choices of GUI including GNOME 2 (or something very close to it).  However both of these are RAM hogs in general, it is nothing to use 2.0-2.2GB RAM with a few tabs open from a newspaper site, even general use usually you would use 1.6-1.8GB  If you have the specs to run it then Ubuntu/Edubuntu is an excellent OS.  

One more note:  if you are running an older computer with less than 2.5GB RAM or a crappy processor I would actually try the lighter OSes such as Lubuntu, Xubuntu or Kubuntu.  I actually chose Lubuntu for my new laptop because it has a very low power processor (AMD E1-2100 1.0GHz) meant more for power conservation than processing power.  I found it ran much better on the lighter distro even with 4GB of RAM.  Lubuntu will run on 1GB of RAM for most applications, certainly no more than 1.5GB RAM would ever be needed using current website technology, my top usage on it was 1.4GB and that was with ten tabs open on a RAM hog site.  You can add about 300MB to these RAM numbers for Xubuntu or Kubuntu.

---

