---
title: "How to clean install"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by FrankBro on 2008-06-28
Ok so i wanted to know how to do a clean install without changing partitions ( using the partition ubuntu is curently on). I want to use the same 20gig ubuntu use atm and the same swap but i want to make SURE my vista partition doesnt get screwed up. Do i just pop the ubuntu cd and remove ubuntu partition, and use the free space a made with that partition to make a new one for 8.04 ? 

Thx

---

### Post by FrankBro on 2008-06-28
i just wanna make sure i dont screw anything up

---

### Post by Crafty Kisses on 2008-06-28
> **FrankBro said:**
> i just wanna make sure i dont screw anything up

This link may help you: [www.psychocats.net](www.psychocats.net)

---

### Post by FrankBro on 2008-06-28
doesnt really answer my question, i know how to install ubuntu. I just want to know how to remove ubuntu and install it again without screwing up my windows partition.

---

### Post by Victormd on 2008-06-28
> **FrankBro said:**
> doesnt really answer my question, i know how to install ubuntu. I just want to know how to remove ubuntu and install it again without screwing up my windows partition.

Just insert the live CD and when you reach the partition editor section, choose manual, and mark the partition that currently has ubuntu to be formatted (there's a tick next to it) and set the mount point as "/" as you did in the first install. For the swap file, simply set the mount point as swap and you're good to go.

As long as you choose the manual option and don't mark your windows partition to be formatted, nothing will happen to it.

---

### Post by FrankBro on 2008-06-28
ok thanks, just wanted to make sure.

---

### Post by Darrious on 2008-06-28
I would go to System->Administration->Partition Editor (A.K.A Gparted)
Then remove it from there.

If you need help on which one to pick then you should take a screenshot (click Prnt Screen button on keyboard), upload here with new post, and hopefully we can tell you what to do from there.

[U]SECOND OPTION:
[/U]Your second option is to always upgrade online or I think you can just pop in disk and it may upgrade while your in the system, maybe when you reboot and install it, but I'm not quite sure.

-Darrious

---

### Post by FrankBro on 2008-06-28
i want to make a fresh install ( have too much crap installed ), i know which partition is the one with ubuntu dont worry :)

---

### Post by Darrious on 2008-06-28
Then I would probably erase and be on your way :)

---

