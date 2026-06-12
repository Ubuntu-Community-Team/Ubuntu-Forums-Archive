---
title: "Number of restarts count"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by wpshooter on 2008-06-30
Why is it that this Ubuntu O/S does not seem to be capable of accurately keeping tracking of the number of restarts that have been done on the computer O/S ?

I had a file system check that ran earlier this weekend saying that it was forcing a file check because the system had been restarted 32 times without a check being done.  And then this morning when I restarted, it ran another file check saying that the system had been started 39 times since a check was ran.  

I had restarted the system several times this weekend but there is absolutely **NO WAY** that I did 39 restarts.  This O/S does not seem to be capable of doing a simple addition operation !!!

Thanks.

---

### Post by hyper_ch on 2008-06-30
do you have multiple harddisks in the system?

---

### Post by starcannon on 2008-06-30
I've often wondered how it counts, a little googling got me this

> When the system boots all filesystems are checked to see whether they are Clean. The term simply means whether the filesystem was unmounted properly after it's last use. If the filesystem is Dirty then fsck will be called in to check it out in more detail. Some Unix variants such as Linux will also run fsck after the filesystem has been mounted N times - N is the maximal mount count.

But still as far as I'm aware I'm not mounting and unmounting my file system while the computer is running, but I'm guessing theres more to it than that. It's counting something, I'm just not entirely sure what. I can go months and months without it happening, then have it happen 4 or 5 times in a row, no rhyme, no reason, at least to my uninitiated mind.

quote was taken from [http://andrew-gray.com/unixfaq/fsck.shtml](http://andrew-gray.com/unixfaq/fsck.shtml)

---

### Post by wpshooter on 2008-06-30
> **hyper_ch said:**
> do you have multiple harddisks in the system?

No, just 1 SATA hard drive.

Thanks.

---

### Post by sayakb on 2008-06-30
```
sudo tune2fs -c 1000000 /dev/sda1
```
Should change the check interval to every 1 million disk mounts.

---

### Post by chrisccoulson on 2008-06-30
It doesn't count the number of times the computer has been restarted. Each filesystem keeps a record of the number of times it has been **mounted**. If you have more than one partition, their counts may all be out of sync and the maximum count values (at which a filesystem check is performed) may all be different too. This explains the behaviour you see. 

What you saw is one partition reaching its threshold of 32 mounts (so that filesystem was scanned), and then a few reboots later another filesystem reached its threshold of 39 mounts.

---

### Post by wpshooter on 2008-06-30
> **chrisccoulson said:**
> It doesn't count the number of times the computer has been restarted. Each filesystem keeps a record of the number of times it has been **mounted**. If you have more than one partition, their counts may all be out of sync and the maximum count values (at which a filesystem check is performed) may all be different too. This explains the behaviour you see. 

What you saw is one partition reaching its threshold of 32 mounts (so that filesystem was scanned), and then a few reboots later another filesystem reached its threshold of 39 mounts.

If I have only 3 primary partitions of /root, /home, & /swap, (jut 1 operating system on computer - Ubuntu) and they were all installed at the same time, how do they manage to get mounted at different points in time other than the booting of the computer ?  I don't think that I have either mounted or unmounted them myself because I would not know how ?

Thanks.

---

### Post by chrisccoulson on 2008-06-30
> **wpshooter said:**
> If I have only 3 primary partitions of /root, /home, & /swap, (jut 1 operating system on computer - Ubuntu) and they were all installed at the same time, how do they manage to get mounted at different points in time other than the booting of the computer ?  I don't think that I have either mounted or unmounted them myself because I would not know how ?

Thanks.

They haven't been mounted a different number of times. They've were given different max count values when they were formatted. One partition has a max count of 32 and the other one has a max count of 39. This means one partition gets checked every 32 mounts and the other one is checked every 39 mounts. This is why they're out of sync.

---

### Post by ayenack on 2008-06-30
To the best of my knowledge if you've got more than one partition on your Hard Drive (which I'm sure you have) it'll check them at different times. It won't check a whole drive at once but instead check the partitions individually and so the count will seem a little odd ball at times.

---

### Post by vanadium on 2008-06-30
For my laptop (one single file system) I have full checking once a month, and checking based on mount count disabled:

```

sudo tune2fs -c 0 -i 1m /dev/sda1

```

---

