---
title: "Switching from Windows - Need Application Advice"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by runningboy01 on 2013-01-16
Hi all,

I've been a traditional Windows user for year.  However, a while back I installed Ubuntu within Windows using wubi.  I explored a bit and became really intrigued.  Didn't spend a ton of time, but really liked the overall "feel" of Ubuntu.

That being said, I'm currently in the middle of doing a computer upgrade and am highly considering switching from Windows as my main OS to Ubuntu.  However, there are some things (programs) that I was hoping to be able to use.  I've done a bunch of searching online trying to find answers, but wanted to post and get input from people that have hopefully been in my position.

The main programs that I need to work would be Games on Steam, Guild Wars 2, and Adobe CS5 Suite.  

I know Steam is now available on linux so I'm thinking I may be OK there.  As for the others, my idea was to run in VMWare Workstation 9.  I have a copy for Ubuntu and was thinking of running Windows 7 (or 8) in VMWare and playing GW2 within it.  Has anyone experienced this to speak on performance?  Same would be true I suppose for any other 3D Game within VMWare?  I would imagine that I could run Adobe CS5 (I mainly use Photoshop and Premiere Pro) within VMWare as well.

Any help/advice/suggestions would be greatly appreciated.

My new computer build will be as follows:

Case - HAF932 Advanced
Mobo - ASUS Crosshair V Formula-Z AM3+ AMD 990FX
CPU  - AMD FX-8120 Zambezi 3.1GHz
RAM  - 8GB G.SKill DDR3 1600
GPU  - Radeon HD 5830 1GB 256-bit DDR5
PSU  - Rosewill RBR1000-M 1000W PSU
SSD  - 128GB OCz Vertex 4
HDD  - (2) 1 TB Drives, (1) 500GB Drive

---

### Post by jerome1232 on 2013-01-16
Virtual machines are terrible for gaming. Based on [this winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=26558") entry Guild Wars 2 has a silver rating in wine and looks playable but has graphics corruption issues. Your best off dual booting for Guild Wars 2 I think.

According to [this winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20158") entry, cs5 works fairly well in wine. There is also Gimp, which is a native photoshop equivalent photo editor. CS5 would likely work very well in a virtual machine.

---

### Post by mad2-814 on 2013-01-16
You can also install steam on wine for the games that haven't been ported to linux yet.

Just install the PlayonLinux package

```
sudo apt-get install playonlinux
```

and browse through there for the games that you are looking for.

I use it for Dota and LoL and they both work fairly well

---

