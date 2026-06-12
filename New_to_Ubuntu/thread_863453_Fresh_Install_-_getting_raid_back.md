---
title: "Fresh Install - getting raid back"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by talking_walnut on 2008-07-18
Hi,

I did a fresh install to 8.04 and now I'm trying to figure out how to get back my software raid. I installed mdadm and rebooted and it seems to have detected the raid alright but isn't mounting it. When I try manually mounting it mount returns "must specify filesystem type" error. 

I've a lot of stuff on the drives I don't want to lose so I'm afraid to go messing around too much in case I accidentally wipe everything. Does anyone know how to fix this?

---

### Post by talking_walnut on 2008-07-18
Update:

/proc/mdstat is reporting the following:
```
md0 : active raid0 sdb[0] sdc[1]
      976772992 blocks 4k chunks
      

```

I'm not sure why it's using sdb[0] as it should be sdb[1]. I presume this might be where the problem is. Can anyone tell me how to fix this without wiping everything?

---

### Post by talking_walnut on 2008-07-19
Bump

Anybody have any advice? I'm completely stuck with this. I've also noticed that neither /dev/sdb1 or /dev/sdc1 seem to exist but the partitions do exist (fdisk shows them). I presume this is part of the problem. Anybody know how to fix it?

---

### Post by CooLGeeK on 2008-07-22
Yes, you're are probably right that you can spot the problem from:
> md0 : active raid0 sdb[0] sdc[1]
      976772992 blocks 4k chunks
What this means is that mdadm found an md superblock on the disk itself (i.e. /dev/sdb and /dev/sdc) aside from the raid partitions (/dev/sdb1 and /dev/sdc1).

_Relative to accessing your data:_
You can try stopping the automatically created device and reassemble the raid array using the right components (i.e. raid partitions) by using the --force option.
```
sudo mdadm --assemble /dev/md0 --force /dev/sdb1 /dev/sdc1
```

_Relative to existence of md superblocks:_
You can try checking for the existence of md superblocks on other disks or partitions aside from the ones you are sure forming a raid array.
For example ...
```
sudo mdadm --examine /dev/sdb
```

---

### Post by talking_walnut on 2008-07-23
Thanks for the reply. Unfortunately since I posted this my hard drive with the os installed got corrupted and one of the fans in the case now sound life a jet engine :( . I've decided to take a break from trying to get it working as otherwise I'll probably pull my hair out in frustration. 

I'll post again when I get a chance to look at everything.

---

