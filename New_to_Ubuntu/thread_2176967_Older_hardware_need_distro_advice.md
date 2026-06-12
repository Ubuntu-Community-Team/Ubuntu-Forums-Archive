---
title: "Older hardware need distro advice"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by michael70 on 2013-09-26
My laptop is older but I have been using Windows XP SP3 for over a year  now and was playing the game League of Legends everyday for hours just  fine. I am hoping to find a suitable Linux distro for my hardware. And  hopefully continue playing League of Legends but with better resources  and better OS.
 
System Specs:
 
Intel Pentium 4 3.2 ghz with 512 kb cache
ATI RV350 Mobility Radeon 9600 128 mb 
1 GB RAM
40 GB HDD
 
I just started learning Linux system and have Linux Mint Debian Edition  with XFCE installed and working. I am wanting to use the laptop for  lower end gaming, youtube and watching live streams via  Justin.tv/Twitch.tv. The trouble I am finding is when wanting to get 3D  acceleration working and installing the Propriety drivers from ATI. I  expect that I am going to settle for an earlier Linux distrobution.
 
I read that Ubuntu 12.04 already had the driver manager and when I tried  the 32 bit version it wouldnt install when clicking the install icon on  Live mode.
 
If someone more Linux distro and hardware savy could help point me into the right direction.

---

### Post by Bashing-om on 2013-09-26
michael70; Hi !

Lubuntu I expect is a prime candidate ! 
Available from "ubuntu community" link at the top of the forum post.
Burn it as a liveCD (md5sum to verity the d/l) and try it - "try ububtu" mode .. see if you like it ..

[INDENT][INDENT]workie great, last long time
[/INDENT][/INDENT]

---

### Post by walterorlin on 2013-09-26
That will run Lubuntu fine I can run Lubntu with 512 mb ram.

---

### Post by mastablasta on 2013-09-27
> **michael70 said:**
> My laptop is older but I have been using Windows XP SP3 for over a year now and was playing the game League of Legends everyday for hours just fine. I am hoping to find a suitable Linux distro for my hardware. And hopefully continue playing League of Legends but with better resources and better OS.

System Specs:

Intel Pentium 4 3.2 ghz with 512 kb cache
ATI RV350 Mobility Radeon 9600 128 mb 
1 GB RAM
40 GB HDD

I just started learning Linux system and have Linux Mint Debian Edition with XFCE installed and working. I am wanting to use the laptop for lower end gaming, youtube and watching live streams via Justin.tv/Twitch.tv. The trouble I am finding is when wanting to get 3D acceleration working and installing the Propriety drivers from ATI. I expect that I am going to settle for an earlier Linux distrobution.

I read that Ubuntu 12.04 already had the driver manager and when I tried the 32 bit version it wouldnt install when clicking the install icon on Live mode.

If someone more Linux distro and hardware savy could help point me into the right direction.

let go back a bit. first your chip:
ATI RV350 Mobility Radeon 9600 128 mb 

is not supported by AMD anymore so abandon hope for proprietary drivers to work because they won't. they dropped support for it quite some time ago. so now you are left with opensource drivers. so with opensource drivers if anyone worked on this chip then it means that latest kernel will give better results.

mint debian is based on debian testing i believe. so the kernel could be relatively new. 
another option owuld be ubutnu and then add ppa for latest drivers. however i wouldn't keep my hopes up. these mobility chips do not have goo opensource support. 

on the other hand i read that in latest kernel AMD made a huge contribution with drivers. might be good to read on new features and check if they cover your GPU chip. 

also for windows based games windows is much better choice than linux. especially with these that have constant updates. 
with LoL i am getting bad FPS even in XP and the card i use is not too bad.

---

### Post by morgan4 on 2013-09-27
I also suggest Lubuntu, it runs so much quicker than Windows on my 3 year old netbook, which is what I use for school and some emulator games while I am traveling.

---

