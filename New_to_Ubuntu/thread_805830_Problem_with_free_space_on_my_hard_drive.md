---
title: "Problem with free space on my hard drive"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Reshuken on 2008-05-24
Hello guys. Well, a few days ago I noticed that the free space on my hard drive is presented differently on the Disk Usage Analyzer and when I'm exploring the drive from Nautilus; Disk Usage Analizer says I have 3.1 GB free, but Nautilus says it's only 2.6 GB. 

In any case, I don't know which is correct, but I would like to see why I have this inconsistency. Thanks in advance!

---

### Post by quelx on 2008-05-24
One is probably reading the raw space available the other is calculating the clusters available

[http://www.answers.com/topic/slack-space?cat=technology](http://www.answers.com/topic/slack-space?cat=technology)

---

### Post by Reshuken on 2008-05-24
Ok, that seems to be possible. A couple of question though: which one should I take for real free space available? And is there anyway to optimize this wasted space so that it can be used as normal?

---

### Post by quelx on 2008-05-24
> **Reshuken said:**
> Ok, that seems to be possible. A couple of question though: which one should I take for real free space available? And is there anyway to optimize this wasted space so that it can be used as normal?

If you format a drive you can force a particular (smaller) cluster size, the drawback is disk performance will be impacted because the accounting overhead needed to keep track of the clusters goes up.  It's a trade off.  You are probably better off rolling with what you have, you won't get that much space back and the price you'll pay won't be worth it.

[http://www.wlug.org.nz/DiskCluster](http://www.wlug.org.nz/DiskCluster)

---

### Post by cdtech on 2008-05-24
df -H from a command line

---

