---
title: "Mirror between disk from command"
date: 2018-05-12
forum: New to Ubuntu
---

### Post by sed_faster on 2018-05-12
I use this code to create a mirror between two disk with the same dimension (ssd: 120GB). But this code is not exactly the mirror, but yes the copy all new files from main disk to second disk (backup disk).

```
cp -auv /home/user/Documents/ /disk/user/120GBMirror/
```

Which parameters or command can I use to create a totaly mirror betewwen disk?

Thanks

---

### Post by dino99 on 2018-05-13
Maybe glance at [https://www.howtoforge.com/local_debian_ubuntu_mirror](https://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by sed_faster on 2018-05-30
Thanks to your help. 
The apt-mirror solve my problem with necessary mirror data between different drives? Can I use this program to do backup data?

---

### Post by mastablasta on 2018-05-31
backup? read again what you wrote.

mirror will copy all files even the corrupted ones to the other disk. so if one disk is corrupted the other will be corrupted as well leaving you with no backup. mirroring doesn't serve backup. it serves us in case of disk failure (though in that case RAID is probably a better solution). 

to backup the data you should use versioning (versions). in command line this is easily achieved with programs such as for example rdiff-backup. there is also rsync and some others. if you prefer a GUi there is plenty of such programs (dejadup, duplicati, backintime, areca...). some use a gui to help you setup the backup, recover the files ... and then they create a script which runs per your specification (for example once a week, once a day and once a month).

---

