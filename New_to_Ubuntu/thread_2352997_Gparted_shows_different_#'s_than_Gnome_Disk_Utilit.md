---
title: "Gparted shows different #'s than Gnome Disk Utility"
date: 2017-02-17
forum: New to Ubuntu
---

### Post by bm0127 on 2017-02-17
Hello all,

Have a question of curiosity, not so much an issue.  I was taking a look at Gparted, and noticed that the capacity of my SSD was not shown as 240GB.  I was not surprised by this, as this is the case with most storage devices. However when I looked at Gnome Disk Utility, it showed 240GB.  Furthermore, each of my partitions appear smaller in Gparted than they do in Gnome Disk Utility. 

[ATTACH=CONFIG]273771[/ATTACH]

Is this normal?  Is there any cause for concern?

I'm running Lubuntu 16.04.2 LTS.

Thanks in advance!

---

### Post by pqwoerituytrueiwoq on 2017-02-17
GiB (1024 base) vs GB (1000 base)
storage manufactures use a 1000 base, most software uses a 1024 base, this is why when you see a 1TB drive it looks like 931.51

---

