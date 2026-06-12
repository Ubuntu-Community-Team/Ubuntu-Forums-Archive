---
title: "[SOLVED] Is this normal for a second Hard Drive ?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by philinux on 2008-05-21
11.8 gig used. Thats a lot of disk space used

---

### Post by SunnyRabbiera on 2008-05-21
well do you have something on your external?

---

### Post by philinux on 2008-05-21
Hi Sunny

No both internal 250gig HD's. Disk one ubuntu, disk two spare formatted with gparted.

---

### Post by SunnyRabbiera on 2008-05-21
so the second drive is blank?
No OS or anything?

---

### Post by philinux on 2008-05-21
Correct

---

### Post by SunnyRabbiera on 2008-05-21
hmm, and you just formatted it to EXT3...
Interesting, I do know that on some hard drives space is held off for stuff but this amount of space used is very... unusual.

---

### Post by philinux on 2008-05-21
Update screen pic from gparted.

---

### Post by SunnyRabbiera on 2008-05-21
That is strange, as gparted is reporting only 2GB used...
now that makes more sense as I know linux needs a base of 2GB at least for allocation and such and can be taught to use something smaller.

---

### Post by deanjm1963 on 2008-05-21
What you have is correct. ext3 takes 5% of disk space for root usage (which can be set to zero, not sure of the command tho as it's not needed for storage space), 250gb is "unformatted capacity", but once it's formatted, with any file system that figure drops. I have a couple of 160gb drives and they format to around 149gb.

hope this helps

---

### Post by SunnyRabbiera on 2008-05-21
> **deanjm1963 said:**
> What you have is correct. ext3 takes 5% of disk space for root usage (which can be set to zero, not sure of the command tho as it's not needed for storage space), 250gb is "unformatted capacity", but one it's formatted, with any file system that figure drops. I have a couple of 160gb drives and they format to around 149gb.

hope this helps

yeh that is what I had in mind.

---

### Post by philinux on 2008-05-21
Thanks guys. Looks like all green to go then.

Ubuntu is the way to go. No other OS comes close at the moment for stability and ease of use . Will be using spare drive as storage.

Many thanks..

---

### Post by buntunub on 2008-05-21
I just got, and formatted a new USB external drive and get the same here. 11+G just gone after partitioning via Gparted.

```
dave@dave:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              36G  3.1G   33G   9% /
varrun                506M  440K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M  496K  506M   1% /dev/shm
lrm                   506M   38M  469M   8% /lib/modules/2.6.24-16-generic/volatile
/dev/sda1              99M   41M   54M  43% /boot
/dev/sdb5              98G   62G   36G  64% /home
/dev/sdb7             9.8G   33M  9.8G   1% /media/sdb7
/dev/sdc1             150G   90G   60G  60% /media/sdc1
/dev/sdb6              42G  1.2G   41G   3% /var
[B]/dev/sdd1              97G  188M   92G   1% /media/disk
/dev/sdd2             201G   48G  154G  24% /media/disk-1[/B]
```



Notice /dev/sdd1, which is currently completely unused as missing 5G, and the other 6G from sdd2, which is less obvious to see, but it is. Searching hidden files reveals nothing as well. sdd1 is formatted as ext3 and sdd2 is my mythtv drive formatted as xfs.

---

### Post by Wandering on 2008-05-21
Don't forget that a drive rated 250 GB is using a decimal rating, 1000 megabytes per GB, where most of the software measuring usage is using GiB 1024 megabytes per GiB.  The often don't bother to specify the 'i' in the unit. So a 250 GB drive will actually yield you about 232 GiB. It's all about marketing and making the drives seem bigger. 

Good luck.

---

### Post by buntunub on 2008-05-21
> **Wandering said:**
> Don't forget that a drive rated 250 GB is using a decimal rating, 1000 megabytes per GB, where most of the software measuring usage is using GiB 1024 megabytes per GiB.  The often don't bother to specify the 'i' in the unit. So a 250 GB drive will actually yield you about 232 GiB. It's all about marketing and making the drives seem bigger. 

Good luck.

:eek:

Thats really quite disconcerting. I had no idea about that.

---

