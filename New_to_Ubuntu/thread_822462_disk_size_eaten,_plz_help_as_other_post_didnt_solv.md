---
title: "disk size eaten, plz help as other post didnt solved"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by akkad on 2008-06-08
my root partition size is eaten but how ???  i dont know , the root partition i have has the ubuntu 8.04 native installation plus the up-to-date updates and some small applications, where even i relocated the users home directory to another partition, but as i can see that the root partition reserves 16GB (as appears in gparted) , when i open the root "/" directory and check the size there by right click on all the folder except the mnt (as i mounted the other partitions there) it show the size is 4GB, where at the moment the disk is full whenever am trying to copy new files, so what this could be?? does the updates installed somewhere (may be in secret place!!) that reserve this size??? if so then should i accept all the updates to be installed (as i usually do) ???

---

### Post by Monicker on 2008-06-08
What is the output of running the following command from the terminal?
```

df -h
```

---

### Post by akkad on 2008-06-08
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   17G  1.2G  94% /
varrun               1013M  264K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   52K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-18-generic/volatile
/dev/sda5             114G   36G   76G  33% /mnt/akkad
gvfs-fuse-daemon       19G   17G  1.2G  94% /mnt/akkad/.gvfs

---

### Post by Monicker on 2008-06-08
> **akkad said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   17G  1.2G  94% /
varrun               1013M  264K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   52K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   38M  976M   4% /lib/modules/2.6.24-18-generic/volatile
/dev/sda5             114G   36G   76G  33% /mnt/akkad
gvfs-fuse-daemon       19G   17G  1.2G  94% /mnt/akkad/.gvfs

You definitely are getting low on space for the /dev/sda1 parition.  You can narrow it down more with the following command:

```
sudo du -ch --max-depth=1 /
```

---

### Post by akkad on 2008-06-08
but why low space while i dont have anything there except the OS files + updates + small apps !!!!!!!

---

### Post by drs305 on 2008-06-08
> **akkad said:**
> but why low space while i dont have anything there except the OS files + updates + small apps !!!!!!!

Have you deleted a lot of large files as root lately? You can find all your system's Trash folders  with the following command and then use nautilus or another file manager to investigate. If you open it with the second command you will be able to delete found files as root:

```

sudo find / -type d -iname Trash
gksudo nautilus &

```

---

### Post by dfreer on 2008-06-08
It could be a log file grew horribly out of control (I had this happen on a server once because a Hard Drive was failing, and it spewed tons of error messages). It could be your apt-cache (a cache of every program you download is stored in /var/cache/apt/archives/) hasn't been cleaned for awhile.

In short, you need to figure out where or what is using all your disk space, and from there figure out why it used it all in the first place. Do the command posted to figure out where your problem is.

---

### Post by akkad on 2008-06-08
drs305 where have u been all that time, yes u are right, it is the trash issue, now this is logic, the root used size is 3GB , thnx and sure am gonna raise a thank for u for this help cuz it was too close for to get crazy if this was not solved, thnxxxxxxx  ...

---

