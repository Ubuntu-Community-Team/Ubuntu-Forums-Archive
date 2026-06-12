---
title: "SD Card CID"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by zahi_k on 2014-07-28
Hello Mates,
I am new to Ubuntu, Like 2 hours :)
I was trying to read the CID of an SD card but this what i get:

zahi@zahi-UBUNTU:~$ /sys/block/mmcblk0/device/cid
bash: /sys/block/mmcblk0/device/cid: Permission denied


any help please?

---

### Post by ubudog on 2014-07-28
Welcome to Ubuntu!

You might have some luck with the following command:
```
sudo cat /sys/block/mmcblk0/device/cid
```

---

