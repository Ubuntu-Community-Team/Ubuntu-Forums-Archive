---
title: "Question: Repartitioning NTFS and reinstalling Ubuntu"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by neksys on 2008-06-09
Hey all,

Just a quick question. I am currently dual booting XP and Hardy, with my 80 gig drive split roughly 50-50.  I would like to reconfigure my system to have XP + 5-10 gigs, Hardy + 5-10 gigs, and the remainder (say 30-40 gigs) shared between them on a separate ext3 partition. 

I am prepared to reinstall ubuntu.

My plan is to delete the existing linux partition, resize the XP partition, create a separate ext3 partition, and install ubuntu in the remaining space.  Thoughts? Ideas? Cautions? Is there a better way?

Greg

---

### Post by JoshuaRL on 2008-06-09
Sounds good, but you'll need to get the driver so that Windows can read ext3 filesystems.  [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by neksys on 2008-06-09
> **JoshuaRL said:**
> Sounds good, but you'll need to get the driver so that Windows can read ext3 filesystems.  [http://www.fs-driver.org/](http://www.fs-driver.org/)

Already installed it - thanks though! I just wanted to make sure there weren't any bizarre issues I might run into.

---

