---
title: "reinstall on /"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by vashwood on 2008-06-02
When I first installed Ubuntu, I installed / on one partition and I put /home on another partition.  How difficult would it be to just reinstall the OS but keep all my stuff on /home?  Is it just a matter of going back through the install and just neglect to install a new /home partition?

---

### Post by maybeway36 on 2008-06-02
Tell the installer that your old /home partition should be mounted on /home, but tell it not to format that partition. (In other words, very easy :))

---

### Post by vashwood on 2008-06-02
THanks.  And that won't erase anything I currently have on there?

---

### Post by avtolle on 2008-06-02
So long as you don't reformat /home partition, no; but, it is always good practice to back it up "just in case", e.g., you have fat fingers like I and hit the wrong key, etc.

---

### Post by Aelfric5578 on 2008-06-02
Make sure you know which partition number goes with which partition (hda1, hda2, sda1, sda2, etc.)  The first time I did this, my two partitions were around the same side and I couldn't remember which was which.

---

### Post by bumanie on 2008-06-02
When I have done it, I don't even check anything to do with my separate /home - I leave it alone. I get the installer at the partitioning stage to install to / and format the / partition. The installer knows that there is a swap partition already allocated so you don't have to worry about that either. It works for me, not sure if it's the 'official' or best way to do it - but it works.

---

