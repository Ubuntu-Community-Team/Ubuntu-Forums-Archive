---
title: "[SOLVED] Formatting an external HDD that has 2 partitions?!?!"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-08-16
I received an external hard drive, but it is partitioned into 2 NTFS drives. I did a format from with windows, but all that did was clear everything in it. does anyone know how i ccan merge the two partitions back together? i am guessing with gparted in ubuntu, but have no experience with it. thanks

---

### Post by Tom--d on 2008-08-16
No, There is no way of merging them together. Once the partitions are made, thats it.

You will need to format the whole drive and made one partition. Gparted will do that.

Back up everything you want on that HDD first ;)

---

### Post by Elfy on 2008-08-16
You could possibly keep one of them and resize it to fill the drive, so if you had data on the first, delete the second and then reisze the first and vice versa.

If they are empty - you can do that or delete and start again as Tom--d said.

---

### Post by deathvalleyjoker on 2008-08-16
ok so i deleted both partitons, but i want to format them as ntfs so windows can reconize it too. but NTFS is greyed out. why is this so?

---

### Post by drs305 on 2008-08-16
I believe the repo version of gparted that runs from within ubuntu does not have that capability. If you use the gparted livecd it is integrated with ntfsprogs, which will allow it to resize ntfs partitions. The ubuntu livecd may have that capability as well - I can't remember.

---

### Post by Too Late on 2008-08-16
You can install ntfsprogs package with Synaptic so that the repo version of gparted will do that thing as well. I'm not sure if something else than ntfsprogs have to be installed, too.

---

### Post by deathvalleyjoker on 2008-08-16
Ok so here wasa my round about way of doing it: 

I used Gparted to delete both partitions and make one big one. I put it in my windows machine but it was unreconized. I then used my windows install disc to go into the area where u can format and partition hard drives before you install windows, and made it a raw data drive. Went back into windows and it reconized it then, so i used windows to format it NTFS. 

I cheated a little and used windows, but it got the job done. I just started using Ubuntu/ Linux this summer, after using windows since the DOS days, so i am alowed to cheat while i am stil llearning :P

Thanks guys!

---

### Post by drs305 on 2008-08-16
I just tried resizing an NTFS partition with the ubuntu livecd version of gparted and it worked fine.

---

### Post by deathvalleyjoker on 2008-08-16
I installed the ntfsprogs, and it is no longer greyed out. wish i would have know that b4 haveing to do my complicated method.

That bugs me about windows: they have the partition and reformat option for when you install window, why couldnt they just keep it in the O/S?

oh well. glad i made the switch to Ubuntu. 

thanks again!

---

### Post by Too Late on 2008-08-16
> **deathvalleyjoker said:**
> That bugs me about windows: they have the partition and reformat option for when you install window, why couldnt they just keep it in the O/S?
Windows (at least XP) does have a partitioning tool. It's somewhere in Administrative Tools/Computer Management.

---

