---
title: "Why do I have space restrictions in my home folders?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by lazercat on 2008-08-21
I have about 1.3 GB of music in my Music folder, but when I try to copy more of my music (about 4.6 GB in total) from a flash drive to the Music folder it says I only have 56.6 MB of space left. I have the same issue with my Pictures folder. It says that I have about 600 MB left of 950 MB of pictures for that folder. How do I get rid of or expand these restrictions? Windows doesn't have them and I bet OS-X doesn't either.

---

### Post by Titan8990 on 2008-08-21
Does /home have its own partition?

---

### Post by Cypher on 2008-08-21
From a Terminal window please show the output of
```

sudo fdisk -l
df -h

```

---

### Post by lazercat on 2008-08-22
[http://i270.photobucket.com/albums/jj107/ChoklitReign/sudofdisk.jpg](http://i270.photobucket.com/albums/jj107/ChoklitReign/sudofdisk.jpg)

---

### Post by shae on 2008-08-22
The partition you put ubuntu on is only 7.0 GB robotsandwich.  You have likely filled up that area and need to make it larger.

---

### Post by lazercat on 2008-08-23
According to my Home folder it has less than 4 GB of space left. So how do I make it bigger?

---

### Post by eightmillion on 2008-08-23
Is this a wubi install?

---

### Post by Loaded.len on 2008-08-23
I was just going to ask the same thing.  Your linux partition is W95.

this is what a df -h should look like on a completely stock Ubuntu install on a 250 GB drive. 

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              14G  3.6G  9.6G  28% /
varrun               1014M  132K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M   48K 1014M   1% /proc/bus/usb
udev                 1014M   48K 1014M   1% /dev
devshm               1014M  116K 1014M   1% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3             215G  132G   83G  62% /home
gvfs-fuse-daemon       14G  3.6G  9.6G  28% /home/don/.gvfs

```

---

### Post by lazercat on 2008-08-23
I have the latter, it's all under my C:\ drive
[http://i270.photobucket.com/albums/jj107/ChoklitReign/df-h.png](http://i270.photobucket.com/albums/jj107/ChoklitReign/df-h.png)

---

