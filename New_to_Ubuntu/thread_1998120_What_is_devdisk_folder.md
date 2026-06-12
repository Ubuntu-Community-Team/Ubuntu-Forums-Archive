---
title: "What is /dev/disk folder"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by mosquetero on 2012-06-06
Hi,

I am trying to learn about storage in linux. I already read about the /dev/ folder which gathers all the devices that are connected to the machine. Those devices are presented as files that define the interface of the device with the kernel. I found that there is a folder called /dev/disk which apparently gives more information about the storage devices. My questions are:

1 - As soon as one storage device is connected and appears in /dev/ as for example sdb, will something be created in the /dev/disk? Or do I need first to give a file system or mount it?

2 Why when I execute "ls" in the folder /dev/disk/by-path I see 4 devices but when I execute "ls" in the folder /dev/disk/by-id or /by-label I see only one? Should it not be the same number and just refer to the same storage device, by path, by ide or by label?

Thanks :)

---

### Post by zombifier25 on 2012-06-06
Like what you said, /dev/disk provides more info about the partitions on your system. Perform a
```
ls -l
```
and it should give you the REAL drives they are pointing at (for example, on my system, /dev/disk/by-label/UBUNTU is actually a symlink to [noparse]/dev/sda8[/noparse]). This would explain why some folders has a few more entries than others (for example, some partition does not have a label assigned, so they will not be listed in by-label)

---

### Post by mosquetero on 2012-06-06
Hi

When I execute ls -l I see four folders:

by-id
by-label
by-path
by-uuid

However, if I access those folders and execute ls -l I see a different number of lines in the output. I expected to see the 4 storage devices I have referred by id, label, path and uuid. Why?

---

