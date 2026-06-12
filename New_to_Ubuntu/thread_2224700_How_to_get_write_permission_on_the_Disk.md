---
title: "How to get write permission on the Disk"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by ram13 on 2014-05-17
I made (using ubuntu) gpt table and ext4 partition on my 3tb hard drive. Afterwards I transferred the hard drive to my windows (different machine) to copy files into them, during this time I did fix broken blocks on this hard drive using Knoppix as below

```
sudo fsck.ext4 -v /dev/sdb1

```

after the file transfer I put back hard drive on my ubuntu machine, now it is just read only. Hard drive is manually mounted to /mnt

how to get write permission? thanks

---

### Post by m1qkus on 2014-05-20
Did you already try the following? 

```
sudo mount -o remount,rw /mnt
```

---

