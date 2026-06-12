---
title: "Hard drive issues"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by buntu_hugenewbie11 on 2008-09-17
I am trying to understand how my hard drive is full because I use an external hard drive as well.
My main linux partition(sda4) is something like 87% full. my /media/ takes up 11.5 gigs on the main drive (sda4) and it is all from my external drive. WTF?
And if I interpret things correctly then most of this fullness comes from mounting an external drive that is an ext3 format. Am I understanding that this is how space is used on the main partition?
Attached is a copy of df -h:
sda4 is the main partition and I definitely do not have 25 gigs of data as I assume linux fits in 5 gigs easily. I have tried everything to lower the sizes as I expect to get about 8 gigs of data shortly. How can I ensure that the harddrive is not having space misallocated. (I have deorphaned things removed older kernals and used localepurge) Any ideas would be helpful.

/dev/sda4              36G   30G  4.5G  87% /
varrun               1008M  140K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  116K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  971M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              35G   14G   21G  41% /media/sda1
/dev/sda2              35G   19G   16G  55% /media/sda2
/dev/sda4              36G   30G  4.5G  87% /media/sdb5
/dev/sdb6              76G   52G   25G  68% /media/ntfsExt

---

### Post by tangibleorange on 2008-09-17
> **buntu_hugenewbie11 said:**
> I am trying to understand how my hard drive is full because I use an external hard drive as well.
My main linux partition(sda4) is something like 87% full. my /media/ takes up 11.5 gigs on the main drive (sda4) and it is all from my external drive. WTF?
And if I interpret things correctly then most of this fullness comes from mounting an external drive that is an ext3 format. Am I understanding that this is how space is used on the main partition?
Attached is a copy of df -h:
sda4 is the main partition and I definitely do not have 25 gigs of data as I assume linux fits in 5 gigs easily. I have tried everything to lower the sizes as I expect to get about 8 gigs of data shortly. How can I ensure that the harddrive is not having space misallocated. (I have deorphaned things removed older kernals and used localepurge) Any ideas would be helpful.

/dev/sda4              36G   30G  4.5G  87% /
varrun               1008M  140K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  116K 1008M   1% /dev
devshm               1008M     0 1008M   0% /dev/shm
lrm                  1008M   38M  971M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1              35G   14G   21G  41% /media/sda1
/dev/sda2              35G   19G   16G  55% /media/sda2
/dev/sda4              36G   30G  4.5G  87% /media/sdb5
/dev/sdb6              76G   52G   25G  68% /media/ntfsExt

you could try using the find command to locate files bigger than a certain size:

```
find / -size +100000k
```

in that example, it should show all files bigger than 100000kB (100MB). you can change the number if too many files are shown, but it should give you some idea as to which file(s) are consuming your drive.

---

### Post by nothingspecial on 2008-09-17
Browse to your internal drive. Press Ctrl + H and have a look in your .trash file. If you`ve not emptied it for a while it`s supprising how much stuff can be in there.

---

### Post by buntu_hugenewbie11 on 2008-09-17
I did the trash thing and it brought me to my current state.
I have done all sorts of removals and purging that is not the issue.
The issue is that my external usb harddrive is taking up 15gigs of space.
Is there a way to mount these drives (ext3) so they won't take up space on my main partition? I have a feeling I messed up how it mounts for this to happen. Any ideas?

---

### Post by buntu_hugenewbie11 on 2008-09-17
When I run that command I get a lot of files on other drives and paritions but I do find one interesting error:
find: Filesystem loop detected; `/media/sdb5' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.

Could this be contributing to the problem?

---

### Post by buntu_hugenewbie11 on 2008-10-06
Bump.
Does anyone know how to investigate the above error?

---

### Post by alphaniner on 2008-10-17
Have you checked root's trash folder?

[QUOTE=buntu_hugenewbie11]Is there a way to mount these drives (ext3) so they won't take up space on my main partition?[/QUOTE]

Mounting drives/partitions shouldn't take up space.  What are you seeing that makes you think this is happening?

[QUOTE=buntu_hugenewbie11]Filesystem loop detected; `/media/sdb5' has the same device number and inode as a directory which is 2 levels higher in the filesystem hierarchy.[/QUOTE]

Two levels higher than /media/sdb5 is /... that's just weird.  Why is sdb5 not in your *df* output?

If I were you I'd *umount* all the partitions in /media.  Better yet, comment them out in your fstab and reboot.  Then mount them one by one and see if you can isolate an issue.

One thing that is probably taking up space on your ext3 partitions is blocks reserved for root.  5% of the partition is reserved unless you specify otherwise, which you can only do with *mke2fs* (AFAIK).  That's only ~1.8 GB on your 35 & 36GB partitions, but its something to keep in mind.

---

### Post by buntu_hugenewbie11 on 2008-12-16
So what happened was that my external drive was mounting incorrectly and sometimes not at all. When this happened sometimes programs would auto save things to the directory where the drive usually mounts in linux. But since it wasn't mounting the drive was just getting filled on my internal drive.
Thanks for the help.
:popcorn:

---

