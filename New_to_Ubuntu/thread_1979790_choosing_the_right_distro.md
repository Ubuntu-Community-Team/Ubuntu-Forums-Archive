---
title: "choosing the right distro"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by H2DAZ on 2012-05-14
Hello there, I wanted to know which distro will be best suited for my comp config

System Manufacturer : Self Assembled
OS : Windows 7 Ultimate build #7600 (32-bit) dual boot with Mac OS X SL 10.6.8 [w/ Darwin boot loader]
CPU : Intel Core2 6300
Motherboard : DG965RY
Memory : 2GB
Graphics Card : NVIDIA GeForce GTS 250
Hard Drives : 1 [160GB]

I want to remove Windows 7 and have Ubuntu installed[dual boot with Mac OS X]. My usage will be watching movies, gaming, browsing the net and running a few bt clients. Also would love to learn how to use the command line interface of Linux

---

### Post by 2F4U on 2012-05-14
You should be able to run most modern distributions. So it mostly comes down to personal preferences.

---

### Post by H2DAZ on 2012-05-14
> **2F4U said:**
> You should be able to run most modern distributions. So it mostly comes down to personal preferences.

How about Ubuntu Desktop 12.04 LTS that i downloaded from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) will this be a good choice for beginners?

---

### Post by sadaruwan12 on 2012-05-14
Welcome to the forums !

According to your specifications you computer is capable of running any distro with out any problem. It's just boils down to what you need and what you plan to do with the distro.

As you've said for movies, internet and bt clients the linux platform is grate and safe but when it comes to games well it's still little sketchy still.

You want have the experience you had with the windows platform 'cos all big games are built for that format but there are ways to run windows games like using WINE, Play on Linux or CrossOver linux but they don't give you the full satisfactions.

Other than the games for any thing else well Linux is safe, fast and secure.

---

### Post by Face-Ache on 2012-05-14
Personally, if you want games, i'd run Ubuntu alongside Windows 7 in a dual-boot configuration, and use Windows 7 for your gaming needs.

I downloaded 12.04, but was getting frequent "Ubuntu has encountered an error" problems. So i'd suggest 11.10, and then maybe upgrade to 12.04 at a later time once a few more updates have been issued that address the bugs.

---

### Post by sudodus on 2012-05-14
> **H2DAZ said:**
> Hello there, I wanted to know which distro will be best suited for my comp config

System Manufacturer : Self Assembled
OS : Windows 7 Ultimate build #7600 (32-bit) dual boot with Mac OS X SL 10.6.8 [w/ Darwin boot loader]
CPU : Intel Core2 6300
Motherboard : DG965RY
Memory : 2GB
Graphics Card : NVIDIA GeForce GTS 250
Hard Drives : 1 [160GB]

I want to remove Windows 7 and have Ubuntu installed[dual boot with Mac OS X]. My usage will be watching movies, gaming, browsing the net and running a few bt clients. Also would love to learn how to use the command line interface of Linux
I would suggest that you make a triple boot system. Keep Windows for games! Ubuntu actually won't need that much space, so you can edit your partitions with gparted to create suitable sizes of partitions for each operating system and for data.

Run a live session of Ubuntu (booted from a CD or USB drive)

1. mount all partitions

2. and post the output of the following commands

a. ```
sudo fdisk -lu
```
b. ```
df
```

This will make it easier to give advice about partitioning.

Concerning distro, version and flavour, I suggest that you either download several of them and try live from CD or USB, or that you download Ubuntu 12.04, test and install it, and then install the other desktop environments, so that you can compare and select what you prefer.

Ubuntu with Unity (or Gnome 3)
Kubuntu with KDE
Xubuntu with XFCE (light-weight and fast)
Lubuntu with LXDE (ultra light-weight and fast)
```

sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install lubuntu-desktop

```
I think you have horsepower enough for any of the desktop environments, but you might enjoy the extra speed with the lighter versions.

---

### Post by H2DAZ on 2012-05-14
Thanx guys for all your thoughts and ideas. Sudodus I will send ya the response to the codes in a couple of days., wont be about for a couple of days due to exams

---

### Post by codemaniac on 2012-05-14
Choose one ..
[www.distrowatch.com](www.distrowatch.com)

---

### Post by DingusFett on 2012-05-15
Yeah as stated, you should be alright to run any distro with those specs. I've had the same issue with choosing after reading about each of them, so I had a Windows 7 partition, and a test partition, installed Ubuntu on the second and installed the different desktops I wanted to try out, gave them each a try out and decided from there. Trying live CD's is good, but for me was significantly slower than once I installed to the hard drive.

---

