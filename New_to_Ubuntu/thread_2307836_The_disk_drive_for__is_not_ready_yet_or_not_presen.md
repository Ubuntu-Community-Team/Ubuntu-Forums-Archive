---
title: "The disk drive for / is not ready yet or not present"
date: 2015-12-28
forum: New to Ubuntu
---

### Post by cafeledavid on 2015-12-28
I have searched online and found a bunch of posts for this boot error however none of them matched my issue

the only thing I did prior to rebooting which started giving me this error was installing ubuntu 14.04 in vmware (i removed it now)
if i do S to skip i can get to the login and desktop but it keeps doing this every time i boot my system not sure what is causing this, i have an external drive connected but i also did a full shut down, unplugged it, and booted with the same error, in fact sometimes when i boot i just stare at a black screen until i do ctrl alt del to reboot manually

i checked the fstab file and it hasnt been modified as i backed that up prior to using vmware and rebooting

thank you

this is what i see when i use [COLOR=#444444][FONT=Helvetica][I]sudo fdisk -l

[/I][/FONT][/COLOR]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005b9b5


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   964716543   482357248   83  Linux
/dev/sda2       964718590   976771071     6026241    5  Extended
/dev/sda5       964718592   976771071     6026240   82  Linux swap / Solaris


Disk /dev/sdb: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f02e15b


is this the culprit? /dev/sda5       964718592   976771071     6026240   82  Linux swap / Solaris

---

### Post by cafeledavid on 2015-12-28
i was able to fix it

i looked more closely at the error and saw the uuid, i figured out that it was my old external drive which i posted about in another thread how permissions got screwed up so i formatted it via windows vmware but ubuntu still had it in the fstab file which is why it was in the backup file too, i put a hash tag to comment it out just in case and tada, no more error on bootup

sucks i deleted my vmware of ubuntu (was going to use for testing) now i gotta re-do it :\

---

### Post by yetimon_64 on 2015-12-29
> **cafeledavid said:**
> i was able to fix it...
It is good you explained how it was fixed, may help others with a similar situation. Could you also please mark the thread as "Solved" from the Thread Tools drop down menu near the top of you browser window in this thread? 

Some help on how to mark your thread solved is [[COLOR=#0000ff]--here--[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), if needed. Regards, yeti.

---

### Post by Skaperen on 2015-12-29
> **cafeledavid said:**
> now i gotta re-do it :\"practice make perfect"

---

### Post by cafeledavid on 2015-12-29
> **yetimon_64 said:**
> It is good you explained how it was fixed, may help others with a similar situation. Could you also please mark the thread as "Solved" from the Thread Tools drop down menu near the top of you browser window in this thread? 

Some help on how to mark your thread solved is [[COLOR=#0000ff]--here--[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), if needed. Regards, yeti.


done

yeah i hate threads where they say they solved it but dont post how and never respond when someone asks, sharing is caring! :D

---

