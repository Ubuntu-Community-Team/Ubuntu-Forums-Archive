---
title: "fsck &amp; how to tell which /dev/ a drive is?"
date: 2020-07-01
forum: New to Ubuntu
---

### Post by nginmu on 2020-07-01
Looking in the unmodified default PCManFM-Qt 0.14.1 on Lubuntu 20.04 I can see under Devices, "32 GB Volume".

Clicking on it shows me /media/me/XXXX-XXXX (XXXX-XXXX is the UUID of the drive)

It's a 32GB SD card currently in the computer's built-in card reader.

I would like to try running fsck -a /dev/sdX on this drive because in PCManFM it shows one empty folder DCIM in which I expected to find another folder named 100MEDIA containing .avi video files, but instead there's nothing.

The card is one I've previously used in the same trail camera successfully a number of times, except, I have previously used Windows to view the files. The card is formatted FAT32.

If I use terminal I get

```

me@me-pc:~$ cd /media/me/XXXX-XXXX/
me@me-pc:/media/me/XXXX-XXXX$ ls
DCIM
me@me-pc:/media/me/XXXX-XXXX$ cd DCIM
me@me-pc:/media/me/XXXX-XXXX/DCIM$ ls
ls: cannot access '100MEDIA': Input/output error
100MEDIA
me@me-pc:/media/me/XXXX-XXXX/DCIM$ 


```

How would I positively identify which /dev/sdX this drive is?


[EDIT]

Sorry I did not google hard enough. 
```

mount | grep /dev/sd

```
mount | grep /dev/sd

---

### Post by sudodus on 2020-07-01
Try with the following command lines, that provide different details,

```

df -h
sudo parted -ls
lsblk -f
lsblk -m
lsblk -o vendor,model,name,size,fstype,label,uuid,mountpoint

```

You can copy and paste the last command line from here to your command line window.

---

### Post by nginmu on 2020-07-01
Thanks, I've looked at those, useful for the toolbelt. Sorry for posting a bit hastily.

---

