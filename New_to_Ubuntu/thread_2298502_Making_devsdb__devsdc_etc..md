---
title: "Making /dev/sdb  /dev/sdc etc."
date: 2015-10-11
forum: New to Ubuntu
---

### Post by dcmcleod85 on 2015-10-11
Hello all,

Just joined a second ago, glad to beer. That autocorrected from "be here" to beer but I'm going to leave it because I'm glad to beer too :D. I'm about to take LXO-103 and 104. I'm following along with some videos and I'm currently on the section discussing Mounting Filesystems. The instructor has constantly brought up these filesystems i don't have. Ironically enough I've learned a lot and he's very good but has yet to describe the simple fact of "hey, this is how you make sdc1 so when I'm telling you about fdisk, you're not spending an additional 10 minutes figuring out how I got sdc1 in the first place" Now from my recent understanding, I use "mkdir"? Then mount the FS to that directory? When I entered that into my Ubuntu machine it gave me seemingly like 10 sdc's, which I don't need to how would I make just like 2? Sorry if this got wordy I'm not fully understanding yet the whole mounting filesystems to directories quite yet.

---

### Post by oldfred on 2015-10-11
Post this:
sudo parted -l

New systems with Windows 8 or later use gpt partitioning which fdisk does not yet support. (Will have some support in 15.10). You use fdisk for MBR(msdos) partitioned drives.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Drives are sda, sdb, sdc. That is physical drives not Windows "drives" which really are partitions.
Partitions then are sda1, sda2, sda3 or the number after the drive letter.

In Windows the d drive can be sda2 (second partition on first drive) or sdb1 (if only one partition on sda and the d is first partition on second physical drive).

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Bucky Ball on 2015-10-12
sda = first drive. sdb = second drive.

sda1 = first partition, first drive. sdb3 = third partition, second drive. And so on ...

Hope that makes sense. sdc3, for instance, would be the third drive, third partition. To create it, you would need to create a partition, not a regular directory. There is nothing stopping you from creating the mountpoint /media/user/sdc1, but I doubt that is what the tutor is talking about.

sdc1 would generally be a partition and you would find it at /dev/sdc1. Run

```
sudo blkid
```

... and see what's there.

(Also 'sudo parted -l' as suggested by oldfred.)

---

### Post by dcmcleod85 on 2015-11-06
I just posted another question and did not realize that my previous question was answered by you two a couple weeks ago. I greatly appreciate it and yes that does make perfect sense now. I also appreciate your tag exclaiming how to mark it as solved. I'm still new to forums in general and don't know the exact etiquette. Thank you again.

---

