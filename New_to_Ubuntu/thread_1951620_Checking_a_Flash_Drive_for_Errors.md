---
title: "Checking a Flash Drive for Errors"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by juliarain on 2012-04-02
I have a flash drive that got slightly wet a few years ago, and I was curious to see if any parts of it were corrupt. It does technically still work. I ran fsck on it, then read the info page for that command, but I still can't interpret the output. Is this even the right thing to do? 

Here is the output from fsck, for what that's worth: 
```
sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Reclaimed 4 unused clusters (131072 bytes).
Leaving file system unchanged.

```

---

### Post by lmarmisa on 2012-04-02
> **juliarain said:**
> I have a flash drive that got slightly wet a few years ago, and I was curious to see if any parts of it were corrupt. It does technically still work. I ran fsck on it, then read the info page for that command, but I still can't interpret the output. Is this even the right thing to do? 

Here is the output from fsck, for what that's worth: 
```
sudo fsck /dev/sdb1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
Reclaimed 4 unused clusters (131072 bytes).
Leaving file system unchanged.

```

Your flash drive seems almost sane. This device is formated with FAT32 file system and its internal data structure is not completely consistent. Some unused clusters could be recovered. 

Try to repair your device typing this command:

```

sudo fsck.vfat -a /dev/sdb1

```

---

### Post by juliarain on 2012-04-05
Thanks! It did reclaim the unused clusters.

---

### Post by codemaniac on 2012-04-05
**badblocks** is a Linux utility to check for bad sectors on a disk drive. It creates a list of these sectors that can be used with other programs, like mkfs, so that they are not used in the future and thus do not cause corruption of data.

There is also this Bad Blocks HowTo by Bruce Allen .
[http://ubuntu-rescue-remix.org/node/50](http://ubuntu-rescue-remix.org/node/50)

---

