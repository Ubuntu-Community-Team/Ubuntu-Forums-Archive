---
title: "Unable to auto mount a drive on startup"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by Philbert579 on 2013-05-04
Hello all, first of all I am running 13.04, and having trouble mounting disks at startup. I did some research and was able to identify my drives by UUID, following the guide at [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions), and was able to successfully create a command to mount both of the drives that I wish to use, which is
```
/usr/bin/udisks --mount /dev/disk/by-uuid/1AD8BF4DD8BF25C3 && /usr/bin/udisks --mount /dev/disk/by-uuid/3ED028B8D02877F3
```
which, when run, does mount both of my drives at /media/xxx.
But, when it is enabled as a startup command, it only mounts one of the disks, the 3ED028B8D02877F3 UUID. Any ideas to make this successfully run?

---

### Post by deadflowr on 2013-05-04
Have you tried running two different/separate start-up application instances?
Make one for each.

---

### Post by Philbert579 on 2013-05-04
Wow! I feel pretty slow for not trying that again. I had done it on 12.10 and never had any success, but splitting the commands up worked fine now that I'm on 13.04 =D> Thanks for the quick reply!

---

### Post by Bucky Ball on 2013-05-04
Welcome to the forums.

To help others please edit first post and click 'Go Advanced' then change the [ubuntu] prefix in the thread title to [solved]. ;)

Please post a new thread concerning any further issues.

---

