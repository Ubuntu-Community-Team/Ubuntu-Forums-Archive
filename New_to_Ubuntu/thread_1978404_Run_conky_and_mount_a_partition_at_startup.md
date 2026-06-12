---
title: "Run conky and mount a partition at startup?"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by Therealmikek on 2012-05-11
I have tried finding some instructions i can follow for mounting a seperate partition and running conky at startup, with no real success. If anyone could give some fairly simple instructions that'd be awesome...

thanks for any help

---

### Post by Enigmapond on 2012-05-11
For mounting the partitions see this:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

For conky, just go to startup applications and create a new entry named Conky with the command conky.

---

### Post by wilee-nilee on 2012-05-11
Put conky in the startup applications use the command conky.

---

### Post by oldfred on 2012-05-11
Welcome to the forums.

Generally you have to make a mount point (what name you want to call it), and add an entry to fstab. But the entry in fstab varies depending on what format the partition is.

Post this and we can give you exact commands to copy & paste into terminal:
```
sudo fdisk -lu
```

Understanding fstab - psychocats is proably the most straight forward.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

