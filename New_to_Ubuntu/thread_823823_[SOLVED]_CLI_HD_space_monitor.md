---
title: "[SOLVED] CLI HD space monitor"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-09
Is there any lightweight program that would check the space I have available on my box?

---

### Post by annda on 2008-06-09
```
df -h
```

will show you availabla space on all mounted partitions. it's not a monitor, but still pretty useful

---

### Post by bluepowder7 on 2008-06-09
i use the system monitor.  it has a tab for your mounted devices / hard drives.

System - Admin - System Monitor - File Systems tab

---

### Post by ilrudie on 2008-06-09
> **annda said:**
> ```
df -h
```will Show You Availabla Space On All Mounted Partitions. It's Not A Monitor, But Still Pretty Useful
+1

---

### Post by AnLGP on 2008-06-09
Thanks that's what I was looking for.  This is the output just so you see:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  1.8G  214G   1% /
tmpfs                 502M     0  502M   0% /lib/init/rw
udev                   10M  104K  9.9M   2% /dev
tmpfs                 502M     0  502M   0% /dev/shm

ahhhh, space!

ps.

why is it that I have 227 and have only used 1.8 gig (plus the MB elsewhere) and it went down to 214 available and not, say, 226?

Is there something that doesn't show up there?

---

### Post by bluepowder7 on 2008-06-09
yeah, if it's ext2 or ext3 or whatever, the space isn't used TOTALLY efficiently, so available space is less than hard drive capacity.  plus, there's usually also a 5% block that's "reserved" to prevent crashes when you get crazy and fill up the hard drive.  either one of those could be why you actually have less space available than you could.

---

### Post by cariboo on 2008-06-09
Remember hard drive manufacturers rate size differently than computers do see this article here:

[http://en.wikipedia.org/wiki/Hard_disk_drive](http://en.wikipedia.org/wiki/Hard_disk_drive)

Check the bottom section called capacity measurements

Jim

---

### Post by nlz on 2008-06-09
try conky!
then you can monitor everything always, from your desktop background. Or de system monitor in the taskbar. (you can add it by right clicking the taskbar)

---

### Post by cdtech on 2008-06-09
I use a script to monitor my drives and if one gets low it sends a text to my cell phone. I use this for my backup drives.

Or if you want to see your drive capacities, use conky for on screen monitoring. It's transparent and can give you a lot of information while your on your computer.

---

### Post by unutbu on 2008-06-09
The output of df is precisely correct if properly interpreted. The bottom line is:
Total = Used + Available + Reserved
df reports Total, Used and Available, but omits Reserved.
Reserved is space reserved for root. If your hard disk fills up completely, it could lock up and be completely unusable. To protect against that, your filesystem reserves space that only root can write to. Normal users will run into trouble first, and thus provide an early warning to root that space needs to be freed. 

I'll use a 2GB USB flash drive as an example:

```
% df /dev/sdb1
                         Total    
Filesystem           1K-blocks      Used  Available Use% Mounted on
/dev/sdb1              1927104      2880    1826332   1% /media/disk

```
Total = 1927104*1024 bytes = 1973354496 bytes
Used = 2880*1024 bytes = 2949120 bytes
Available = 1826332*1024 bytes = 1870163968 bytes
```

% sudo tune2fs -l /dev/sdb1
Reserved block count:     24473
...
Block size:               4096

```
Reserved = 24473*4096 = 100241408 bytes

Total = Used + Available + Reserved
1973354496 = 2949120 + 1870163968 + 100241408

---

### Post by AnLGP on 2008-06-09
Thanks :).  I love conky but can't figure out how to get it configured plus it's not entirely transparent on JWM for me anyway.  Thanks for the list on HDDs.

---

### Post by unutbu on 2008-06-09
```

Filesystem Size Used Avail Use% Mounted on
/dev/sda1  227G 1.8G 214G    1% /

```
/sda1 has about 11.2GB of reserved space. This is enough space for an entire Ubuntu installation! The idea of reserving 5% of a disk made sense when hard disks were 10GB, but nowadays, with 250+GB hard disks, the 5% default has become ridiculous. 

To reset the reserved space to 1% (~2.3GB), you can run
```

df
sudo tune2fs -m1 /dev/sda1
df

```

To reset the reserved space to 1GB (equal to 244140 4K-blocks), you can run
```

df
sudo tune2fs -r244140 /dev/sda1
df

```

(Run df because it's fun to see the difference.)

---

### Post by AnLGP on 2008-06-09
I just clicked the required install on the debian .iso and CLI my entire system from the ground up.  heh.

so what'll those commands do in laymans terms?

---

