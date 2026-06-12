---
title: "Partitioning"
date: 2014-03-20
forum: New to Ubuntu
---

### Post by ray9 on 2014-03-20
I installed Ubuntu on a 500G hdd and let it have the whole disk.  I see now that wasn't a good idea.  /dev/sda1 is taking up 462.01 MB.  Is there anyway to split that in half w/o re-installing?

---

### Post by QIII on 2014-03-20
Hello!

If you just chose "Use entire disk" that isn't necessarily bad.  You didn't create a separate /home.

Could you post the results of 

```

sudo fdisk -l

```

That's a small "ell", not a one.

---

### Post by ray9 on 2014-03-20
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968912895   484455424   83  Linux
/dev/sda2       968914942   976771071     3928065    5  Extended
/dev/sda5       968914944   976771071     3928064   82  Linux swap / Solaris

---

### Post by QIII on 2014-03-20
Let's have a look at

```

sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

---

### Post by ray9 on 2014-03-20
NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           465.8G            
&#9500;&#9472;sda1 ext4     462G /          
&#9500;&#9472;sda2            1K            
&#9492;&#9472;sda5 swap     3.8G [SWAP]     
sr0            1024M

---

### Post by QIII on 2014-03-20
OK.  Nothing surprising there.

Since you used the entire disk instead of specifying partitions, that's normal looking.

If you would like to separate your /home out (on this machine I have / at 30GB, no swap because this is a desktop with 32GB RAM and I don't suspend, and the rest of the 1TB disk as /home) [this]("http://psychocats.net/ubuntu/separatehome") might be of interest to you.  I don't know when aysiu last updated this, but I don't think much will have changed.

Otherwise, just enjoy what you have now!

Best wishes.

---

### Post by ray9 on 2014-03-20
Thank you for the replies.

---

