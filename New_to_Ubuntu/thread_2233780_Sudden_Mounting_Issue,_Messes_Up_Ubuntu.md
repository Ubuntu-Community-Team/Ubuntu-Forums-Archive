---
title: "Sudden Mounting Issue, Messes Up Ubuntu"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by mezasemaster on 2014-07-10
Hello,

I am using Ubuntu on my Chromebook for Steam, which necessitated mounting an external hard drive, and after days of work I was finally able to get it to work for a few weeks. During the process, I managed to have the hard drive automount (or something that functions like automount) on startup, but when I did it this way I couldn't use the Steam library in Steam, I'm not exactly sure why. So after that I managed to get it to automount properly by editing the fstab file and have it work with Steam, but that original attempt, which henceforth I'll refer to as the "dud," remains. This only caused a single issue in that, for whatever reason, Ubuntu gave preferential treatment to the dud on startup, so every time I started it up it would automount to that so I'd just have to open a terminal and type "sudo umount -a" followed by "sudo mount -a" to have it properly mounted. Ever since I got to this point I have not messed with mounting at all, but starting today some strange things occur following the proper mount of the hard drive through the terminal:

1. Although I can properly log into Steam and use the friends feature, there's no internet connection in the Steam browser and trying to access anything internet-related in a game will instantly come up with a message saying that it failed to connect, implying that it doesn't detect my internet connection.
2. I cannot access files saved to Chrome OS even though I normally can.
3. The time of the system jumps four hours ahead, which I'm assuming is the system switching from EST with daylight savings in effect to UTC for whatever reason.

It's very odd, again I have not messed with mounting since the initial setup and it's been working fine for weeks, but now it suddenly starts to flip out following the "sudo mount -a" step. Also, since I forgot how I set up the dud mount, I don't know how to disable it from starting (I did a force delete of the folder after I got the mount I wanted working through fstab, but it just gets re-created every time I start up). The dud mount may not even be related, that's just a guess. I'm sorry for the lack of information, I know that's usually necessary in solving these types of issues, but I honestly don't know what to post. If there's any information that you think could help, please let me know.

Thank you!

---

### Post by Bucky Ball on 2014-07-10
Could you please post this file:

```
sudo /etc/fstab
```

Thanks. Presuming your internet is working fine everywhere else, just not with Steam?

PS: Are we talking straight Ubuntu 14.04 LTS? Please confirm.

---

### Post by mezasemaster on 2014-07-10
Okay wait, huge development. I just tried it and it looks like I was wrong - it's not re-mounting the drive that's causing the problem, it's actually *unmounting the dud* that is! I was mistaken because I always re-mount directly after unmounting, so I assumed that was what caused the problem. Additionally, right after typing in "sudo umount -a," I get the following messages:

umount: /run: device is busy.
(In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))
umount: /tmp: device is busy.
(In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))
umount: /dev/shm: device is busy.
(In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
(In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
(In some cases useful info about processes that use the device is found by lsof(8) or fuser(1))

I'm not certain whether I got these messages when unmounting prior to these problems, but I believe that I did not. I should also emphasize that not only did I not mess with any mounting stuff since I got it working weeks ago, but I haven't adjusted any coding or files at all since then sans screenshots and updates through Steam, which should have all been done through my external hard drive anyway.

---

### Post by mezasemaster on 2014-07-10
> **Bucky Ball said:**
> Could you please post this file:

```
sudo /etc/fstab
```

Thanks. Presuming your internet is working fine everywhere else, just not with Steam?

PS: Are we talking straight Ubuntu 14.04 LTS? Please confirm.Well, based on this new development, it seems that the fstab file is unrelated since the problem seems to come from unmounting my "dud" mount, which was made before I ever touched the fstab file. Also I checked, the internet doesn't work at all through Ubuntu outside of connecting to Steam and using the friends list, but Chrome OS isn't affected. It looks like what I'm using is something called "Xubuntu 4.10," which I launch by typing "sudo startxfce4," if that helps. I believe it's all up-to-date.

---

### Post by Bucky Ball on 2014-07-10
Still like to see it and please reread my last post. It has been edited.

* With no internet on the machine that is going to be difficult. You are on cable or wireless? Try a cable.

---

### Post by mezasemaster on 2014-07-10
Well okay, but I believe it's unrelated since the problem comes from unmounting a drive not mounted through fstab in the first place:> /dev/disk/by-uuid/54D8D96AD8D94ABE/ /mnt/My\040Book/ ntfs-3g defaults,auto,uid=scott,gid=0,umask=000 0 0That's all related to the working mount that I'm not having any problems with. I already responded to the edit, the only information I could find is what I posted. Also, Ubuntu works fine prior to unmounting the dud, so I can get internet on here so long as I don't do that. :)

---

### Post by Bucky Ball on 2014-07-11
Not the whole fstab file. Never mind. :-k

---

### Post by mezasemaster on 2014-08-07
Bump, still need help with this. :(

I believe I set the "dud" up through something like the the instructions [here]("https://help.ubuntu.com/community/AutomaticallyMountPartitions"), since it mounts under my username in the "media" folder. So if I could just find a way to undo this, it should be good. However, I don't believe I ever used the "udisks tool" it mentions.

---

### Post by mezasemaster on 2014-08-07
Whoo, I removed the dud! :D Turns out I did have that udisk thing, but for some reason it had a few extra letters attached to the end so I had to type in something slightly different for it, then I just put "unmount" where it says to put "mount" in the instructions for setting up and now it's gone for good! Just one more question though - every time I start up Ubuntu, I still have to type in "sudo mount -a" in the terminal to mount my drive from the fstab file, is there any way I can make it do that automatically?

---

