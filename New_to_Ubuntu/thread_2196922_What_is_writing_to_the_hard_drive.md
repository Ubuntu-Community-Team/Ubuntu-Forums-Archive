---
title: "What is writing to the hard drive?"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by sam_baker2 on 2014-01-01
when I do a 
```
sudo iotop -a

```

I notice that something is more often than not writing to the hard drive,
similar as given in this example:

```
TID  PRIO  USER   DISK READ   DISK WRITE  SWAPIN    IO>      COMMAND
287  be/3  root    0.00 B      304.00 K    0.00  %  0.27%    [jbd2/sda1-8]

```
with the disk write constantly increasing.

Anybody know what it is and what it is for?

---

### Post by TheFu on 2014-01-01
Log files?
Things happen on Linux systems all the time, so writing to log files will happen all the time too. Perhaps a firewall log? Check for file timestamps in /var/log/

swap? - doesn't look like any swap is being used, but if you have a swap file, it can be written to almost anytime.

Everyone I know had this question at some point and researched it too.  I did.  Taught me much.

---

### Post by philinux on 2014-01-01
It's journaling. 

[http://ubuntuforums.org/showthread.php?t=1985454](http://ubuntuforums.org/showthread.php?t=1985454)

See a net search for ubuntu jbd2/sda

---

