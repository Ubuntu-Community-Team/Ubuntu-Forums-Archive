---
title: "PLZ HELP!!!: aMule + Movie Download = no more HD space"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by LiamGaerity on 2008-07-06
Okay,

So I've probably done something really stupid, but I cannot figure it out. I left aMule running last night and when I went back to my computer this morning my Hard Drive was completely full. I've tried find the "offending" file, but to no avail. From the output below, it's obvious that my Hardy partition sda6 is completely full. I do have a separate partition devoted to large files, musics, downloads and such called /media/Personal Files. As you can see, again, from the output below, this partition still has plenty of space.

```
 df -h|grep /
/dev/sda6              34G   34G     0 100% /
varrun                1.8G  120K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G   80K  1.8G   1% /dev
devshm                1.8G   12K  1.8G   1% /dev/shm
lrm                   1.8G   38M  1.7G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/sda9             2.1G  2.0G   25M  99% /media/DellMedia
/dev/sda2              61G   32G   29G  52% /media/WindowsPartition
/dev/sda8             102G   34G   69G  33% /media/Personal Files
overflow              1.0M   36K  988K   4% /tmp
gvfs-fuse-daemon       34G   34G     0 100% /home/thayer/.gvfs

```

Can anyone please help me figure out what's wrong?

Cheers.

---

### Post by huwnet on 2008-07-06
There should be a [disk usage analyser](http://www.howtogeek.com/howto/ubuntu/check-your-disk-usage-on-ubuntu-with-disk-usage-analyzer/) program in your default Ubuntu install so you can find and delete whatever is taking up the space ;)

---

### Post by Steveway on 2008-07-06
Files downloaded with amule should be in:
~./aMule/Incoming
and inclomplete files are in:
~./aMule/Temp
Try looking there.

---

### Post by LiamGaerity on 2008-07-06
Thanks for the responses. I'm using the disk usage analyzer, but and I see that my home directory is full, but I still can't find the file. I've check aMule's Incoming and Temps folders. There's nothing there that will fill up my entire hard drive. Anymore suggestions...?

---

### Post by cariboo on 2008-07-06
In a terminal type:

```
du -h
```

This will print out a listing of all the files in your home directory with their size.

You may want to pipe it to a text file so :

```
du -h > files.txt
```

That is if you have enough room for a small text file.:)

Jim

---

### Post by LiamGaerity on 2008-07-06
Okay, here's what it was. Actually had nothing to do with aMule. Turns out that since I've been using the program Simple Backup to backup my hard drive to my 1 TB external hard drive, I had the program setup to backup daily. Now, since I didn't always have my laptop connected to my external drive, the file would be backed up to my Ubuntu Partition, under /Media/External Hard Drive, and hence, completely filling up my hard drive. 

Thank you all again for your responses.

Cheers.

---

