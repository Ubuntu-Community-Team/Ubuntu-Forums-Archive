---
title: "gzip, tar process in sudo top command?"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by vikka on 2012-07-10
Hello,
By using "sudo top" command , the first things is my list shows as follows.
Gzip taking up 100% cpu, isn't this weird or have i misunderstood? :/

Last time i ran gzip was a few hours ago running a system backup but that one is already done.
PID    USER  PR  NI  VIRT     RES   SHR   S   %CPU   %MEM    TIME+        COMMAND
 3319 root         20    0     8800    664     432   R    100       0.0           97:50.55    gzip
 3318 root         20    0    20416 1536  1104 S   18         0.1           17:16.39    tar
> 
top - 14:44:09 up 18:21,  1 user,  load average: 1.57, 1.67, 1.68
Tasks:  84 total,   2 running,  82 sleeping,   0 stopped,   0 zombie
Cpu(s): 49.2%us,  8.6%sy,  0.0%ni, 42.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1921904k total,  1809068k used,   112836k free,    62644k buffers
Swap:  1961980k total,        0k used,  1961980k free,  1571992k cached
Thanks,

---

### Post by SeijiSensei on 2012-07-10
No, that's perfectly normal and a good thing, actually.  Running gzip is a processor-intensive task; you'd want the operating system to devote as many CPU cycles to the compression process as possible.  If some other process needs the CPU, Linux will balance the requests.  If you let top run and force the machine to do something else while gzip is running, you'll see the other process get some CPU time when it runs and the amount allocated to gzip fall.

---

### Post by asmoore82 on 2012-07-10
I would guess the backup has a bug where it says it's done while still running in the background. If you know the processs ID's you snoop some more information about how they were ran like this:

```
sudo cat /proc/3318/cmdline
sudo cat /proc/3319/cmdline
```

---

### Post by vikka on 2012-07-10
Hi guys,
Thanks for the quick reply and information, yes it seems as if the backup is still running even if nothing is written to the log, which was were i looked. 
My way of doing this test-backup looks as following, and it is supposed to backup the entire system:

(really weird that it is still running since the system is only about 2-3 gigs at the moment)

#!/bin/sh
clear
sudo tar -cvpzf /backups/full-backup.tar.gz / >> /shellscripts/logs/full-backup.log


Cronjob is set to run at 13:01 , at it seems to still be writing to the .tar file.. don't know why :S

> 
-rw-r--r-- 1 root root 740720640 Jul 10 15:28 full-backup.tar.gz


---

### Post by SlugSlug on 2012-07-10
you need to add some --excludes 

a search on here will show you how to backup via tar

---

### Post by vikka on 2012-07-10
> **SlugSlug said:**
> you need to add some --excludes 

a search on here will show you how to backup via tar
Hi,
I know how to do the excludes but hence i want a full system backup, shouldnt it be sufficient with my example?( / for backing up the entire system) Sure there is mounted drives of around 2TB but they've little to no content at the moment.

Been going for around 4 hours plus now , shouldn't take that long to backup 2-3 gigs which is the total system size ?

---

### Post by SlugSlug on 2012-07-10
Yer with out your excludes your backup will never end :)

your currently backing up your backup ;)

You need to exclude where your backing up to 

also exclude /proc /dev and /sys 


a search on here will explain all

---

### Post by vikka on 2012-07-11
> **SlugSlug said:**
> Yer with out your excludes your backup will never end :)

your currently backing up your backup ;)

You need to exclude where your backing up to 

also exclude /proc /dev and /sys 


a search on here will explain all

Thank you :)
Problem solved.

---

