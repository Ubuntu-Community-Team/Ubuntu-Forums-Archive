---
title: "[SOLVED] Renaming Filesystem"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by YldGuy on 2008-08-17
I am not sure where to post this so I am posting it here. Also, I had searched the forum for this but couldn't find a conclusive answer.

I want to rename my Filesystem to something meaningful like Ubuntu. I have 3 ext3 partitions including Filesystem. I set the label for the other two partitions using e2label. Can i do the same with the Filesystem? Will it break anything in there? The reason I am asking is because the other two partitions were earlier mounted like media/disk and media/disk-1 and after i set the label it is now referred as media/Data and media/Media, Data and Media being the labels i gave. So, it essentially renamed the mount point also. Since the root partitions mount point is "/" and its named as Filesystem, will e2label command change the mount point of Filesystem? I am afraid to rename my Filesystem using e2label lest i break my machine. I love its performance and setup and don't want to take the pain of installing everything all over again. 

Any help appreciated.

---

### Post by Sef on 2008-08-17
I would not rename the file system, unless you were willing to reinstall the system.  Also back up your data, so you dont' lose it.

---

### Post by ibutho on 2008-08-17
e2label does not change mount points, it only changes the label of a partition. As for whether this will break anything, it depends on your setup. Some distros use the label to identify partitions in /etc/fstab, but Ubuntu uses UIDs, so chances are that renaming the partition label to "ubuntu" won't make a difference.

---

