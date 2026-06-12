---
title: "Dual booting Ubuntu/WinXP - Partition Reccomendations?"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by covaloch on 2008-05-17
Hi my T60 laptop has a 120gb harddrive (i'm estimating about..100 or so gigabytes for actual use).
I've been using Ubuntu exclusively for the past 4 weeks and I find it absolutely amazing. However I screwed up my laptop when i tried to install Ubuntu Studio by just typing that in synaptic and checking EVERYTHING to install and download. As I'm a complete Linux baby, I think i may have checked something i wasnt supposed to check. 

I intend to do a full reformat and Dual Boot this time.

What I intend to do with my laptop: 
_Ubuntu_:
All my study/office **work**.
**Surfing**
**Sound editing/photos**

_Windows_:
**Sound editing/photos **(i'm still a GimP noob so i need photoshop still. I need Ableton live for sound stuff as well.)
**Games** - WorldofWarcraft DUH! (i'm such an addict)(Ps: Friend tells me Wine support is relatively ok but the framerates are terrible)
**Worldwide Telescope** - I love astronomy. And for all you Microsoft Haters who like to swap the S with a $ sign, i DO know of the existence of Google Sky. But Worldwide Telescope is so MUCH better. You have to try it. If you have a system with Windows. (PS: /rant And yes, Worldwide telescope has been in development way longer than Goggle Sky, just that sky came out first, but albeit rather flawed. So stop the whole "ms copies everything" routine which i see so often on these forums. Very childish /rant off)

As you can see, the Sound/games portion is a shared requirement for both OSes to handle. So i'm thinking i need a file system that can be used by both. Perhaps a partition just to store Videos/Photos/Music

I'm uncertain of how Ubuntu stores downloaded programs, where it stores it, how well it'll handle FAT, whether using FAT is bad for Linux, ad infitum. I was actually thinking of just 20 GB for Win XP, and then a sizeable portion for my "file cabinet" of sorts for the pictures/music/videos, and another portion for Ubuntu.I'm not sure how much i need for that though. And i'm utterly confused by needing a swap partition, etc etc, so please explain if you are able to. Much thanks!

---

### Post by laffinet on 2008-05-17
Based on your needs I'd recommend the following:

1 partition for Windows (your 20 Gig sound alright)
1 partition for Ubuntu (ext3 would be the recommended filesystem, size: I've got 20 gig for that, but I'm only using about 6 at the moment, so less will do as well)
1 swap (size: twice your main memory, filesystem is set automatically when assigned as swap)
1 partition for all your data (as big as you want it. I'd recommend FAT32, windows can read ext3 with extra drivers, but you need to install them. Ubuntu can read FAT32 out of the box. Easier)

All this can be changed later via gparted if needed.

Swap partition: basically, when you run multiple programs and it all becomes too much for your main memory, this is where Ubuntu puts it. Same thing exists in Windows, but I forgot what it's called there.

---

