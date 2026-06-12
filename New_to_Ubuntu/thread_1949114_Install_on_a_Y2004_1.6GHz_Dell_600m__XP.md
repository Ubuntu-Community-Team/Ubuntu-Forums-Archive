---
title: "Install on a Y2004 1.6GHz Dell 600m  XP?"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by alparker on 2012-03-29
[SIZE=2]I have a Dell 600m laptop (circa 2004) windows XP machine with 2G memory and 1.6GHz processor that I want to install Ubuntu to. I need to maintain XP and its files/apps. I have various old XP engineering tools/applications installed that are not replaceable without a lot of effort and need to be maintained. I just tried installing/running the WUBI version. It was so slow that it is basically unusable. The delay between clicking an "OK" or "close" to when it reponds is at least 5-10 seconds.[/SIZE]
[SIZE=2]Will the the non-WUBI install run significantly faster, or should I just give up on this machine. In addition to wasting alot of time trying the full install, I'm concerned about the non-zero chance I will lose my XP functionality do to some install glitch. The other alternative is going out and buying a new/cheap laptop that I can wipe out.[/SIZE]
 
[SIZE=2]So I guess my two questions are:[/SIZE]
 
[SIZE=2]1) Will the full (non Wubi paritioned) install run much faster?[/SIZE]
[SIZE=2]2) What is the probability that my XP will get creamed accidently with a full non-Wubi side-by-side install?[/SIZE]

---

### Post by TeoBigusGeekus on 2012-03-29
1) Yes, but not with Ubuntu; try Lubuntu instead.
2) None, if you're careful enough. Just select manual partitioning during the partitioner stage of the installation. Also, do a thorough defragmentation of your drives before installing (L)Ubuntu (3 or 4 times and preferably with Defraggler). Finally, backups have saved many people from accidents...

---

### Post by CharlesA on 2012-03-29
+1 to backups. What was the saying.. if you don't have backups, you don't care about your data?

If you have a backup and something gets hosed, you can always go back to the backup and be back at a place where you can try again.

---

### Post by koll on 2012-03-29
i think i am using the same laptop as you a latitude d600 i have had problems with version 11.10 installing  only half way and crashing thus corrupting the file system of the laptop i found that installing version 11.4 of Ubuntu then upgrading worked fine hope this helps

---

### Post by Gleichsnerd on 2012-03-29
+1 again to backups. I've lost entire music collections in my ignorant days due to a lack of caution and a fidgety partition table.

I would definitely go (L)Ubuntu install over Wubi, unless you like sticking your finger in the socket for fun.

The installation process is pretty secure in preventing any accidental overwrites of old partitions (unless you accidentally select the "Erase Windows and Come to the Dark Side" option).

So, in short, go for it. But back it up first.

---

### Post by alparker on 2012-03-30
[SIZE=2]Thanks. I installed (10.04 LTE) with XP side-by-side and everything went OK and it runs fine speed-wise.
 
I read on some other threads that 10.x was faster than 11. so I burned a CD with that. I was surprised that when I "try"d Ubuntu (running from CD) that it ran great speedwise, much faster than installed Wubi 11x. I guess WUBI is just slow. I doubt it was because of the 10.x but I didn't try the 11x from the CD.
 
Note I was concerned about losing various installed XP programs, not my files (which I of course have backed up). Before installing I disabled XP paging, hibernation, system restore, then defragged + chkdisk a few times using the XP tools.
 
One minor issue is that I had planned to use more than the 20GB for the Ubuntu (~40GB was free). I selected the default "side-by-side" installation and thought that it would ask about changing the partition size on the next screen, but it didn't. I guess that's what 'advanced" does, but I'm not sure why changing the partition size is "advanced". I did see that you could obviously change the 20GB on the advanced, but I believe the layout shown for the advanced (order and name of the partitions) was different than the default I didn't feel like looking up what this meant, so I took the safe route (it was late).
[/SIZE]

---

