---
title: "need an os to......."
date: 2008-07-09
forum: Other OS Talk
---

### Post by n8ek on 2008-07-09
mount a hard drive that was not shut down correctly by windose

I have been given a laptop where the motherboard has gone and need to retrieve what i can off the HDD, i tried using Mint live cd but kept getting an error message and cant log in as root  to mount the HDD on live cd, is there an OS that will ignore the fact that a HDD was not shut down correctly

Thanks

---

### Post by bigken on 2008-07-09
easy use gparted in ubuntu and force the mount it tells you what to do

you could also use the ubd4win google it

---

### Post by damis648 on 2008-07-09
Ubuntu can do it. Open a terminal and:
```
sudo mount -t ntfs-3g /dev/xdxx /media/disk -o force
```
, replacing "xdxx" with sda1, hda2, or whatever the drive listing happens to be. (Most likely sda1, but you never know)
Also replace "3g" with the generation of NTFS. (ntfs=2000, ntfs-2g=XP, ntfs-3g=Vista) (i think... just plain 'ol ntfs will probably do.)

---

### Post by Twitch6000 on 2008-07-09
gparted live cd is what you need =].

---

### Post by n8ek on 2008-07-09
Thanks for the replies i tried sudo mount -t ntfs-3g /dev/xdxx /media/disk -o force replacing "xdxx" with sda1 and i get "mount: mount point media/disk does not exist"

so i tried gparted live cd in graphics mode and thats as far as i got there was no option to mount, the only live cd i have is mint and gparted, is there something i am doing wrong?

Thanks

---

### Post by bobdob20 on 2008-07-09
> **n8ek said:**
> Thanks for the replies i tried sudo mount -t ntfs-3g /dev/xdxx /media/disk -o force replacing "xdxx" with sda1 and i get "mount: mount point media/disk does not exist"


That means you have to create the directory. Try:

```
 sudo mkdir /media/disk 
```

Then try to remount.

---

### Post by n8ek on 2008-07-09
> **bobdob20 said:**
> That means you have to create the directory. Try:

```
 sudo mkdir /media/disk 
```

Then try to remount.

Thanks bobdob20 that did the trick

---

