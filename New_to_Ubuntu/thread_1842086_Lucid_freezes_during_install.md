---
title: "Lucid freezes during install"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by snip3r8 on 2011-09-10
I have this old Fujitsu Siemens Amilo D 7850 that hates  windows(literally you cant install it).But that's besides the point(i  don't want to install windows anyway),Karmic installed just fine but now  its outdated,My Internet connection is capped so upgrade over net isn't  an option.The problem is when i try doing a fresh install of either  Lucid or Maverick it freaks out when i have to enter my details,as soon  as i hit the first character on the keyboard,it acts as if the key is  held down and i get a username of dddddddddddddddddddddddddd....
and the installation freezes.

is there a way to install in text mode with the live cd?

PS: if i boot the live CD the operating system works just fine

---

### Post by fabricator4 on 2011-09-10
> **snip3r8 said:**
> is there a way to install in text mode with the live cd?


Not with the live CD, but the installer that comes with the alternate-install CD is text mode.

I don't recommend on-line release upgrades as a general rule.  They're slow, and when they go wrong they _really_ go wrong. It also leaves you withough a CD to re-install if you need or want to.

It sounds like the keyboard detection might be going wrong.  Do you have another keyboard you could try with the LiveCD?

An idea out of left field:  Try booting with the keyboard unplugged.  Run as much of the install as you can with the mouse, then plug in the keyboard and wait for it to autodetect, and see if that works.  Also, maybe unplug the keyboard after booting the LiveCD, then plug it  back in again.


Chris.

---

### Post by snip3r8 on 2011-09-10
Its a laptop,but you gave me an idea.Im going to try using external keyboard and see what happens

---

### Post by snip3r8 on 2011-09-10
Ok installation was a success,other issues in boot though,maybe maverick was aiming too high,will try Lucid.

---

### Post by fabricator4 on 2011-09-10
> **snip3r8 said:**
> Ok installation was a success,other issues in boot though,maybe maverick was aiming too high,will try Lucid.

Yah, Maverick had a few issues (the dual boot installer, configuring fstab, startup disk creator), which I thought were fixed later.  I'm not sure what made it onto the LiveCDs though.

Lucid LTS is still my preferred release.  Rock solid on any machine I throw it on, and well, it is the LTS.  Make sure you get the -3 LiveCD (the current one on the download site) as it benefits from over a year of steady improvements and fixes.  If you already have an older CD though, updates will do the same thing.

Make sure you check the MD5sum of the downloaded ISO also.  I've had a couple of corrupted ISO downloads that could have caused a lot of problems if I hadn't checked them first.

Chris.

---

### Post by snip3r8 on 2011-09-10
Already have Maverick,havent missed a distro since 9.10

---

