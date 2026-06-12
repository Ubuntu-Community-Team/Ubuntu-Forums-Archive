---
title: "External USB - Unable to Mount - No Authorize - Headless Machine"
date: 2014-03-17
forum: New to Ubuntu
---

### Post by amb1s12 on 2014-03-17
Hi, I have a Linux headless machine which I have a nomachine server on the ubuntu 12.04 and client on my mac. I went thru this tutorial to be able to get gnome on my headless machine. Now, I'm able to remote, but when I try to access the external drive, I get unable to mount not authorize. The issue i sif I have a monitor on the machine, I'm able to use those drives. I really appreciate if I  anybody can help me with this issue Thanks.

---

### Post by steeldriver on 2014-03-18
What tutorial? can you post a link? 

Do you just want to mount the drives? or do you really want to mount the drives using gnome specifically?

---

### Post by amb1s12 on 2014-03-18
Here is the link of  the tutorial [https://www.nomachine.com/AR10K00710](https://www.nomachine.com/AR10K00710) . Let me explain what I really want to do. This server main purpose is been a media server. I have plex media server on it and I would like to add a movie folder that I have on the external hard drive.

---

### Post by steeldriver on 2014-03-18
That seems like a sledgehammer to crack a nut

To permanently mount an external hard drive all that you need to do is 

[LIST=1]
[*]identify it, preferably by its UUID using blkid or its disk label 
[*]create an empty directory somewhere of your choice as the mount point; and 
[*]add an entry something like 
[/LIST]
  ```

UUID=4BA80B1E330BA809  /mnt/Seagate    ntfs    defaults,nofail 0 0

```

to your /etc/fstab file (of course adjusting the filesystem type as appropriate - my example drive has an NTFS filesystem).

---

### Post by amb1s12 on 2014-03-18
I'm new with ubuntu, so I don't know what do I have to use with the sample. here is my drive in for:

/dev/sdc2: UUID="535f721d-1ddf-3abc-bff6-d326100afde5" LABEL="HD2" TYPE="hfsplus"

---

### Post by amb1s12 on 2014-03-18
Is there a way that I can get authorize to do all this when using nomachine. The problem is that I'm not getting authorization to do all of this while using a remote desktop tool nomachine.

---

### Post by sandyd on 2014-03-18
Add the following to /etc/fstab
```

UUID=535f721d-1ddf-3abc-bff6-d326100afde5 /mnt/disk1 hfsplus defaults 0 0 
```
assuming that /mnt/disk1 exists and is where you want to mount the disk

---

