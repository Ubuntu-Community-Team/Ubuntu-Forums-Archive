---
title: "Is there anyway to speed up apt-get installs?"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-07-28
I noticed that a dist upgrade after the download seems to take over 2hours or more to install. Anything I can do to speed this up? Ive seen things to speed up download but not actual install.


edit. I mean eather the dist-upgrade, and or install. I havent read up on these in a while I guess there diffrent.

---

### Post by vasa1 on 2012-07-28
> **cosmoshell said:**
> I noticed that a dist upgrade after the download seems to take over 2hours or more to intall. Anything I can do to speed this up? Ive seen things to speed up download but not actual install.
Do you have ample free space? It's possible that there's very little free space on your computer and so installation, in particular, is being affected. Just a guess!

---

### Post by cosmoshell on 2012-07-28
> **vasa1 said:**
> Do you have ample free space? It's possible that there's very little free space on your computer and so installation, in particular, is being affected. Just a guess!


No but on computers with ample space its always been the same. I dont think it has to do with the hardrive.

---

### Post by madjr on 2012-07-28
> **cosmoshell said:**
> I noticed that a dist upgrade after the download seems to take over 2hours or more to intall. Anything I can do to speed this up? Ive seen things to speed up download but not actual install.

*dist upgrades* and *apt-get install some app* are two very different things.

---

### Post by wildmanne39 on 2012-07-28
Hi, dist upgrade does take a long time, it is quicker to do a clean install after backing up important data and much safer.
Thanks

---

### Post by cortman on 2012-07-28
Your download speed will be displayed in the lower right hand corner of the terminal; check it. If it's very low you might try changing repository mirrors. If it's quite high and still taking forever it may be an HDD problem, but I doubt it.

---

### Post by cosmoshell on 2012-07-30
The download speed is great, would be cool if Where dependency are satisfide and still downloading if it started installing immidately, or if possible install more then one at once. I remember years ago there was initNG and at the time it was faster for booting. I just figured there would be a tweak or mod to speed up install.

---

### Post by Sandertje on 2012-07-30
Dist upgrades can take hours. Mine (from 10.04 to 12.04) took about 3 hours in total.

---

### Post by dodo3773 on 2012-07-30
> **wildmanne39 said:**
> Hi, dist upgrade does take a long time, it is quicker to do a clean install after backing up important data and much safer.
Thanks

This ^^

My opinion is that it is always better to do a clean install between distro versions.

---

### Post by IWantFroyo on 2012-07-30
Dist-upgrade is slow.

If apt-get itself is slow, then go to the Software Center, Edit -> Software Sources, and scan for the best download mirror.

---

### Post by vasa1 on 2012-07-30
> **madjr said:**
> *dist upgrades* and *apt-get install some app* are two very different things.

Agree. The title and the content of the question don't match up.

---

