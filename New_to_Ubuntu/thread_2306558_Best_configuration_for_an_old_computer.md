---
title: "Best configuration for an old computer"
date: 2015-12-16
forum: New to Ubuntu
---

### Post by HBG on 2015-12-16
Hello guys, it is my first time using Ubuntu and I'm liking a lot so far. My computer is very old, and because of that I feel some things could be better, I would appreciate some help to make the best configuration for my PC.

It is a Intel Core2 Quad CPU Q6600 @ 2.40GHz × 4 with a graphic Gallium 0.4 on NV96, 64-bits.

Thanks in advantage!

---

### Post by sudodus on 2015-12-16
Welcome to the Ubuntu Forums :-)

A computer with core2quad is quite capable. I think you can try any of the Ubuntu flavours, at least if you have enough RAM (2 GB or more). The main difference is the desktop environment. Try them live before you decide which one you prefer.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

You can find what to do with old hardware in the following link (and find out that it is possible to use older computers too)

[Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by cwmoser on 2015-12-16
My PC is older than yours.  Mine is a dual core AMD Athlon X2 6400.
But, I have upgraded with a Solid State Drive (SSD) for / and /home, and just recently
upgraded to an nVidia GeForce 8800GTX (still an older card).

The SSD made a big difference, and the upgrade of the video card really improved video performance.

I run Ubuntu 15.10 and it performs very fast.

---

### Post by QIII on 2015-12-16
I run the Xfce spin of Fedora on an old laptop with a Core2 Duo and 3GB.  It runs very well. (I also have a small SSD installed, and even with a SATA I, the improvement in disk R/W latency gives it wuite a kick!)

I had Ubuntu on a Core2 Quad with 4GB for quite some time and it ran well.  (It's running Win 10 now.)

I even had Lubuntu on an Odroid XU4 for a while to test performance with a DE, and it performed well.  It's now running Ununtu Server as a web development platform.

For Ubuntu, your limitation is likely to be the graphics adapter more than anything else.  If Unity is too much for it, try Xubuntu or Lubunu to ease up on the GPU demands.

---

### Post by grahammechanical on 2015-12-16
I am getting an acceptable performace from an Intel Core 2 Duo 2.40 GHz with 1 GB Ram and an Nvidia GT220 with 1 GB video memory.

Gallium 0.4 = the open source video driver. NV96 = Nivida code name for a series of Geforce video cards. User experience with Ubuntu depend a lot on how much video memory the adapter has. In my opinion 512 MB and above is preferable. You can go to System Settings>Software & Updates>Additional Drivers tab and install a Nvidia driver. You need a connection to the internet and you need to allow the utility to find the video drivers.

Do not think about installing the very latest Nvidia drivers. It is a good bet that Nvidia has dropped support for that card from it latest drivers. That is what they did to my card and it is a later card than the one that you are using. But Additional Drivers should offer you a legacy driver.

But a lot will depend on the capabilities of that card and its amount of video memory.

[http://nouveau.freedesktop.org/wiki/CodeNames/](http://nouveau.freedesktop.org/wiki/CodeNames/)

Regards.

---

### Post by scottbomb on 2015-12-16
Hardware can be kept useful much last longer with Linux because the OS doesn't drop support for older hardware like Windows does. 

I recently gave away an old Lenovo laptop that had a Core 2 Duo and 2 GB RAM. It runs Kubuntu 14.04 without a problem. Anything much older than that and I'd recommend Xubuntu. The lightest desktop seems to be Lubuntu. I only say this from my own experience where I can get LXDE (Lubuntu) to run on a Beaglebone but not XFCE (Xubuntu).

---

### Post by oldrocker99 on 2015-12-17
I have a 10 year old Lenovo with a dual-core 32-bit **Pentium** with pre-Sandy Bridge graphics, and Ubuntu MATE flies on it. Just about *any* Linux distribution will run better than any Windows OS. MATE is at least as lightweight as LXDE or XCFE, and is a lot more configurable, and has better (IMHO) utilities than other desktop I've tried. It's an official Ubuntu flavor, too. Try it out on a live disk or USB, and see whether you like it.

---

### Post by NM5TF on 2015-12-17
I have to agree with MATE....either Ubuntu or Mint will work very well on older machines....

I am running Mint MATE, Fedora 22 MATE, and Arch Linux on this desktop that is almost
9 years old now....just a dual core AMD with 3.5 GB RAM and nvidia 6150 video card...I
do prefer the XFCE4 DM over Gnome as it uses less system resources....

experiment to see what works best for your machine....

---

### Post by danny_w2 on 2015-12-18
Just my response

That is quite capable
However for the old computers for fast speeds I would run Xubuntu 14.04, not 15.10
That computer should run 14.04 LTS very nicely

[EDIT] Actually, I wouldn't run 15.10 + you should experiment. I would also recommend Linux Mint Cinnamon Edition
Linux Mint is based off of Ubuntu so you should not have any problems

---

### Post by Sweet_Baby_Jamie on 2015-12-20
I run [LXLE]("http://lxle.net") happily on a *very* old desktop with only 512 RAM!  My laptop with similar specs to yours runs Xubuntu with ease.

---

### Post by kurt18947 on 2015-12-20
Piling on here. That machine should run any of the *buntus if it has adequate RAM - 2GB+. I had a 1.5 Ghz. notebook with 3 GB. RAM standard Intel video and it would run Ubuntu-gnome and Linux Mint/w Cinnamon desktop nicely. I wasn't gaming or doing demanding work like video transcoding but for day-to-day usage it was fine.

---

### Post by HBG on 2015-12-20
Thanks guys, very useful insights from you all. My RAM is only 1GB, I think I'll need to add at least one GB more to have it running as I like. I've already did some changes like reduce the swap, put interface in 2D and a few more things, but I still feel the need foram RAM.

---

### Post by kurt18947 on 2015-12-21
> **HBG said:**
> Thanks guys, very useful insights from you all. My RAM is only 1GB, I think I'll need to add at least one GB more to have it running as I like. I've already did some changes like reduce the swap, put interface in 2D and a few more things, but I still feel the need foram RAM.

I've purchased RAM off Ebay with good success. I make sure it's returnable and as soon as I get it I install it - remove what's already there - and run memtest x86 found on Ubuntu install media. Let it run for several hours or overnight. If not errors are found, I'm good. You do need to make sure you get the correct stuff.

---

