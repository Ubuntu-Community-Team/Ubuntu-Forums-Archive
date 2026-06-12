---
title: "Warning mssge &quot;Filesystem-root only 1.1 GB&quot; But FileBrowser says &quot;2.7 GB FreeSpace&quot;"
date: 2016-04-05
forum: New to Ubuntu
---

### Post by swarup on 2016-04-05
I periodically receive a warning message from Ubuntu OS saying "Low Space: Filesystem-root only 900 mB" or "Only 1.1 GB". But then when I check my Nemo File Browser, it says there is 2.7 or 3 GB free. Why does the information I am receiving from these two sources differ?

---

### Post by v3.xx on 2016-04-05
What about..

```
df -h
```

---

### Post by grahammechanical on 2016-04-05
Any OS needs space to work in. If free disk space gets too small then the OS may not even load. The OS creates log files as it loads. It needs a variable amount of space to be used on different occasions. It has folders that need to vary in size and efficiency is better if the disk space is in contiguous blocks rather than scattered all over the disk. The file system (Ext4) is designed to limit disk fragmentation by reserving space for our documents to grow into. It is called Extents

[https://en.wikipedia.org/wiki/Extent_%28file_systems%29](https://en.wikipedia.org/wiki/Extent_%28file_systems%29)

 I would be very surprised if an OS did not make a claim for disk space which it sets aside for potential future use.

The file manager knows nothing of this. It is only counting sections of the disk that have data in them and then doing a subtraction calculation.

Regards.

---

### Post by swarup on 2016-04-05
```
:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G  4.0K  3.8G   1% /dev
tmpfs           773M  1.7M  772M   1% /run
/dev/sda5        71G   64G  2.9G  96% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none            3.8G   85M  3.7G   3% /run/shm
none            100M   80K  100M   1% /run/user
/dev/sda1       197M   21M  177M  11% /boot/efi

```

---

### Post by v3.xx on 2016-04-05
Yes, there is a system reserve.  Something like 5% of your file system.

Still I wonder if you have any large, unnecessary files.

```
find . -type f -size +500M -exec du -h {} \; | sort -n
```

---

### Post by swarup on 2016-04-05
```
~$ sudo find . -type f -size +500M -exec du -h {} \; | sort -n
[sudo] password for swarup: 
2.5G	./Desktop/Material Needed to put on New 14.04/evolution-backup.tar.gz
2.7G	./.thunderbird/fybwsdv8.default/Mail/pop.sprynet.com/Sent
508M	./Desktop/boot-repair-disk-64bit.iso
```

---

### Post by v3.xx on 2016-04-05
There are other things to try,

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

but you may find that a larger partition is needed.

---

### Post by mastablasta on 2016-04-07
> /dev/sda5        71G   64G  2.9G  96% /

If you can try moving some of the more static data that doesn't get much access (pics, video, documents and such) to another disk (external if necessary). you really need more free space.

furthermore, ext4 file system on root disk doesn't work so good when it's loaded above 70%. it slows down a lot. the issue is similar in windows with it's NTFS system. for that reason it would be best to free up at least half of your disk space. and if you don't have space to add a larger hard disk or to increase partition on existing disk, then add external disk and move the files that are not accessed constantly to it. you will have more free space on system disk + it will all work a bit faster (more responsive).

---

