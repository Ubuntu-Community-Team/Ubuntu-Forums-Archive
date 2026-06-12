---
title: "clean install Hardy with 3 partitions"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by corkscrew on 2008-05-13
I have upgraded my laptop to Hardy Heron using the alternative cd route no problems at all.
I want to do a clean install on my desktop though. It is a dual boot machine. I have gutsy on it already with 3 partitions / home and swap. Do i need to anything to these before i do a clean install i have nothing i want to keep except maybe my graphics driver since it was a bit of pain getting set up. All my data is on another drive which is shared with win xp.

---

### Post by anuban on 2008-05-13
I will say since you have a separate /home partition, so you don't have to worry about anything.
When you reach the partition screen, do the following:

Select the partition you want to load Ubuntu on.  Mount it as '/' and select 'Format'.
Select the partition which contains your /home, edit partition and mount it as '/home'.  Don't select 'Format' this time.
That's it.
You should be all set with your existing data.
But to be on the safer side, I will suggest to take a backup of your valuable data.

Hope it helps.

Thanks

---

### Post by corkscrew on 2008-05-13
are my gprahics card drivers and settings in the /home partition then?

---

### Post by Joeb454 on 2008-05-13
I don't think the graphics card drivers are in ~/ (home) though Usually all the application settings are :)

---

