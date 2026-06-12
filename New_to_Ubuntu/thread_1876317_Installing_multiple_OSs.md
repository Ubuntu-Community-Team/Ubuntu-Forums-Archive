---
title: "Installing multiple OSs"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by marenkar on 2011-11-06
Hey guys,

So I wiped my 250 GB Hard drive and I want to install Windows 7, Xubuntu, Ubuntu and Fedora.

-I've tried multiple ways of doing this but this is what I got now:

-I have 200 GB allocated to Windows 7. 25 GB via Wubi of Xubuntu. The rest on Ubuntu. 

-Because I can only have one ubuntu installation via Wubi, I had to use the rest of the Hard Drive for Ubuntu.  I planned to just do some further partitioning through Fedora.

-However, there seems to be a problem. When I boot my computer, I can only select between Windows 7 and Xubuntu. Ubuntu doesn't come up anywhere. 

Previously, I tried installing Xubuntu and Ubuntu both on their own dedicated partition and not via Wubi. However, it would boot straight to Windows 7 without giving me a choice. 

Any ideas?

---

### Post by twtduck.ii on 2011-11-06
If you can afford it with memory and cpu, I'd just install them on Virtualbox. If you can figure out how to I suggest finding out which is lightest and installing virtualbox on that, so that the whole is as fast as it can be. Hope it helped!
Twtduck.ii

Edit:
In other words, if you have an average/slow computer, uninstall Windows (if possible) and run it from virtualbox in one of the three linuxes (they look about the same system requirements), along with the other two. If you want to go to extremes, download the fedora LXDE spin or lubuntu and use that, as LXDE is faster then gnome or XFCE. If you have a higher-end computer, install the linuxes on Virtualbox in Windows.

---

### Post by HalfEmptyHero on 2011-11-06
You don't really need a separate installation for Xubuntu/Ubuntu, you can have both on the same install. Just do sudo apt-get install xubuntu-desktop, or sudo apt-get install ubuntu-desktop.

That being said, I've never used wubi so can't help you there. I would recommend ditching wubi and just have a windows partition, an Ubuntu/Xubuntu partition, and then a Fedora partition.

---

### Post by marenkar on 2011-11-06
Thanks!! I think I'll do that. Would I be able to choose the kind of desktop I'd be using every time I boot? 

I initially just had Windows on there and then later installed Ubuntu 11.10, but when I restarted my computer, it went straight to windows. This was without Wubi and I had Ubuntu on it's own partition and Windows on it's own as well. Any ideas on what could be going on?

Basically this is what I did (different from the occurrence above):

Step 1: Install 100 GB of Windows 7.

Step 2: Install 30 GB of Ubuntu 11.10.

However, when I rebooted, I went straight to Windows 7.

---

### Post by HalfEmptyHero on 2011-11-06
Yes, you will be able to choose which one you want to log into at the login screen. There will be a button of some sort; it'll look different depending on which display manager and which login theme you had, but it will be somewhere. Just click on the buttons till you find it, it will give you a choice of GNOME, Ubuntu, Xubuntu, etc. The Xubuntu one might be labeled as XFCE though.

Did you install grub? Try holding down shift right after your bios goes away, maybe you will see the grub menu show up.

---

### Post by marenkar on 2011-11-06
Sweet! Awesome, I'll do that right as I get this other problem cleared up.

Hmm, I thought GRUB was supposed to install itself automatically with the installation of Ubuntu 11.10? If not, how am I supposed to do it? I've installed 6.06 and 10.04 so this is my first non-LTS release. I haven't really had to install GRUB... well at least I don't remember it.

---

### Post by marenkar on 2011-11-06
> **twtduck.ii said:**
> If you can afford it with memory and cpu, I'd just install them on Virtualbox. If you can figure out how to I suggest finding out which is lightest and installing virtualbox on that, so that the whole is as fast as it can be. Hope it helped!
Twtduck.ii

Edit:
In other words, if you have an average/slow computer, uninstall Windows (if possible) and run it from virtualbox in one of the three linuxes (they look about the same system requirements), along with the other two. If you want to go to extremes, download the fedora LXDE spin or lubuntu and use that, as LXDE is faster then gnome or XFCE. If you have a higher-end computer, install the linuxes on Virtualbox in Windows.

Hmm, I think I'll try virtualbox out if the other way suggested doesn't work. I think having separate dedicated partitions would be better. But this seems like a nice backup plan. Thanks!

---

### Post by marenkar on 2011-11-06
> **stranger_rupz said:**
> plz help me how can i install.

Use an administrator account, that should solve the problem...in theory.

---

### Post by sharks on 2011-11-06
Try running it with Admin permissions? (Run as Administrator)

---

### Post by anewguy on 2011-11-06
> **stranger_rupz said:**
> plz help me how can i install.

And open your own thread instead of hijacking this one.

---

### Post by anewguy on 2011-11-06
And now back to the thread at hand and the original poster, marenkar:

You should avoid wubi for anything other than a simple test drive.  It wasn't meant for more than that.  That's what dual-booting, VM's, etc., are for.

As far as grub goes, and multiple OS's, each time you tried to install another OS did you get an updated grub menu?  You should be able to create separate partitions for each OS and as long as update-grub was run you should see them all.  Just remember partition limits and go for logical (extended) partitions for everything after your 1 partition for Windows and a partition for some Linux install.

Dave ;)

---

### Post by marenkar on 2011-11-06
Thanks!

I didn't see any GRUB menu when I installed Ubuntu 11.10 or Xubuntu (whether it was the first Linux OS or second, it didn't come up).  I just repartitioned again and I realized that I may have messed up on the mount part when I selected to manually partition stuff myself. What am I supposed to enter on there? I entered "/" last time. I also selected ext4. While I have installed ubuntu numerous times in the past, this is the first time I'm doing multi os and manual partitions.


Edit: 11.10's partitioning seems quite different from 11.04 (your installation guide that I checked). I remember seeing that bubble where it states that it will let you choose upon booting up, it doesn't seem to be there on 11.10.

---

### Post by HalfEmptyHero on 2011-11-06
> **marenkar said:**
> Sweet! Awesome, I'll do that right as I get this other problem cleared up.

Hmm, I thought GRUB was supposed to install itself automatically with the installation of Ubuntu 11.10? If not, how am I supposed to do it? I've installed 6.06 and 10.04 so this is my first non-LTS release. I haven't really had to install GRUB... well at least I don't remember it.

Yes, it should. But sometimes things mess up during an install, so who knows. Did you try holding down the shift key after your bios screen goes away?

---

### Post by HalfEmptyHero on 2011-11-06
> **marenkar said:**
> Thanks!

I didn't see any GRUB menu when I installed Ubuntu 11.10 or Xubuntu (whether it was the first Linux OS or second, it didn't come up).  I just repartitioned again and I realized that I may have messed up on the mount part when I selected to manually partition stuff myself. What am I supposed to enter on there? I entered "/" last time. I also selected ext4. While I have installed ubuntu numerous times in the past, this is the first time I'm doing multi os and manual partitions.


Edit: 11.10's partitioning seems quite different from 11.04 (your installation guide that I checked). I remember seeing that bubble where it states that it will let you choose upon booting up, it doesn't seem to be there on 11.10.

Yes, putting a "/" partition is required, and ext4 is a good choice for it. / is your root partition, where your system is installed to, so without it you have nothing.

The installer is different, but there should still be a section where it says "Manual set up drives" or something similar to that. I can't remember exactly where it is, but I'm going to download the ISO for it now to poke around on it.

---

### Post by marenkar on 2011-11-06
> **HalfEmptyHero said:**
> Yes, putting a "/" partition is required, and ext4 is a good choice for it. / is your root partition, where your system is installed to, so without it you have nothing.

The installer is different, but there should still be a section where it says "Manual set up drives" or something similar to that. I can't remember exactly where it is, but I'm going to download the ISO for it now to poke around on it.

Thanks! I'll give it another shot. Please let me know what you find and I appreciate you taking the time to help me.

Update: Wiped my hard drive clean and started from scratch. Installed Windows (160 GB) then I installed Ubuntu 11.10 regularly (selecting the most basic option of having it run alongside Windows). It still goes straight to windows right after booting.

---

### Post by anewguy on 2011-11-06
> **marenkar said:**
> Thanks! I'll give it another shot. Please let me know what you find and I appreciate you taking the time to help me.

Update: Wiped my hard drive clean and started from scratch. Installed Windows (160 GB) then I installed Ubuntu 11.10 regularly (selecting the most basic option of having it run alongside Windows). It still goes straight to windows right after booting.

Are you saying a wubi install or a true dual-boot install?

---

### Post by marenkar on 2011-11-06
> **anewguy said:**
> Are you saying a wubi install or a true dual-boot install?

I did a true dual-boot install.

I got it to work now, but I didn't solve the problem per se. 

I removed Ubuntu 11.10 and installed Ubuntu 10.04 LTS. After installing, I just updated it to 11.10. I think my 11.10 installation disc was just somewhat corrupted in the bootloader component. It looks fine now and I'm running the magnificent 11.10! 

It's not over yet though, I'm still going to install Fedora. But not after getting GNOME and Xfce.

---

