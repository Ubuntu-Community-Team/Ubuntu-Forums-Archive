---
title: "Possible to upgrade with desktop cd?"
date: 2010-03-31
forum: North Carolina Team - US
---

### Post by mark_k on 2010-03-31
I downloaded lucid's beta-1 cd for testing out a fresh install, and all went well.

Now that I have the cd, is there a way to upgrade a machine that already has karmic up to lucid by using the CD? I'd prefer not to put additional load on the download servers (and my pipe) if I've already got the CD. And, I expect to upgrade a couple more machines. I figured I'd save bandwidth if I could.

Thanks!
Mark

---

### Post by markthecarp on 2010-04-02
> **mark_k said:**
> I downloaded lucid's beta-1 cd for testing out a fresh install, and all went well.

Now that I have the cd, is there a way to upgrade a machine that already has karmic up to lucid by using the CD? I'd prefer not to put additional load on the download servers (and my pipe) if I've already got the CD. And, I expect to upgrade a couple more machines. I figured I'd save bandwidth if I could.

Thanks!
Mark

I'm 98% sure you can't upgrade from any live cd. I upgraded a machine from karmic to lucid earlier this week and can say you don't have to worry about using up your bandwidth. It took about 11 hours to upgrade 1764 packages; the highest speed I saw was around 120 kb/s, most of the time it was dialup speed. Painfully slow.

A caveat: know where grub is installed on karmic. You'll be asked where you want the new one to be installed. Most common place is (hd0). I messed up by choosing (hd0,1) and ended up with a broken grub and had to reinstall it (grub2).

hth,
-mark

---

