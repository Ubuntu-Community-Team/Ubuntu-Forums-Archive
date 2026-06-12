---
title: "What does this cron job do and do i need it??"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by woodsta on 2012-07-22
Hey all,

Been using linux a while but am by no means an expert, I've noticed spikes in CPU utilization on a half hourly basis and found a cron job running at the exact times so figure this is the cause but i have no idea what it's doing or if i need it.  so if anyone and translate this into something i can understand and action id appreciate it, the cron job is running:

[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

Cheers

Woodsta

---

### Post by ikt on 2012-07-22
[http://ubuntuforums.org/showthread.php?t=884606](http://ubuntuforums.org/showthread.php?t=884606)


> **MJN said:**
> However, as Tim says, this cron job is PHP doing some housekeeping (purging expired sessions) hence I suggest you leave it be.

---

### Post by richpri on 2012-07-22
The cron /etc/cron.d/php5 job should run every half an hour to purge session files in the /var/lib/php5/ directory.

---

### Post by woodsta on 2012-07-23
Thanks Guys that is useful and good to know but do we think that this script should really max out the Processor? and is there a way to throttle the resource it uses?

Cheers

---

### Post by woodsta on 2012-07-24
Nevermind - did a bit of searching around and found 
[http://ubuntuforums.org/showthread.php?p=11456671](http://ubuntuforums.org/showthread.php?p=11456671)

deleted fuser as noted and bingo problem goooone!:popcorn:

---

