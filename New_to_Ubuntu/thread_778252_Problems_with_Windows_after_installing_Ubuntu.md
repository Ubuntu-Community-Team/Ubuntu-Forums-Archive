---
title: "Problems with Windows after installing Ubuntu"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by jhermes on 2008-05-01
Hello everyone,

I just installed Ubuntu 7.10 on my HP DV9000t this afternoon. I really like it, and once I get the kinks worked out I'll probably use it more than Windows.

I have one main problem - in Windows the system.exe process is constantly using 50% of CPU (one core of my processor) and I have heard that can be caused by a swapfile that's too small or corrupted. The partitioning didn't go exactly as I had planned, allocating 200+ GB of my second hard drive (320GB) to the Linux filesystem. That I can fix, I'm just wondering if the swapfile could have gotten messed up during the partitioning. Anybody have any advice?

I know about as much about partitioning and boot records as I do about ballet...so if I've got it all wrong just say so:)

---

### Post by axor1337 on 2008-05-01
how big is your swap file   i recomend at lease doule your amount of ram or 2Gb what ever is more.  if you think your swap is corrupt the i recomend downloading UBD[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)   and re format your swap part with gparted  and see if that works but if you are running vista it may bee a glitch in the reporting code

---

### Post by ubnoobie on 2008-05-01
have you tried turning the pagefile in windows off and then back on again? (try system managed size to start with)

---

### Post by cubeist on 2008-05-01
> **ubnoobie said:**
> have you tried turning the pagefile in windows off and then back on again? (try system managed size to start with)

Right, if the pagefile is missing or not working correctly windows will not like that...especially vista which is such a ram hog it could barely run without a pagefile (pagefile is sort of like a swap file but on the same partition as windows)

---

### Post by Spoken on 2008-05-01
> **cubeist said:**
> Right, if the pagefile is missing or not working correctly windows will not like that...especially vista which is such a ram hog it could barely run without a pagefile (pagefile is sort of like a swap file but on the same partition as windows)

+1

---

