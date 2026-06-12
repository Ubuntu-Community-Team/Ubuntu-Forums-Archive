---
title: "log files"
date: 2019-03-28
forum: New to Ubuntu
---

### Post by kashei on 2019-03-28
hi

my PC freezes, so im trying to find a log file, to c what was going on before it freezes but i can't find it and i looked in   " root /var/log/"
i can see from dates before and the current log but right before it freezes i cant 
for example i had to reboot my computer at 1148am (it froze) so i can see everything that is happening after that time and i can c log file of my boot up this morning around 8am  and days before, but how do i find a log file between 8am boot and 11:48am reboot 

thank you

---

### Post by Dennis N on 2019-03-28
There is a journal kept by systemd which records much activity.

**journalctl -b** shows you messages from the last boot
**journalctl -b -1** shows you messages from the boot before the last boot.
**journalctl -k -b** shows you kernel log messages from last boot. 
errors may be in red.
see **man journalctl** for many other options.

sudo is not needed for these.

---

### Post by kashei on 2019-03-28
> **Dennis N said:**
> There is a journal kept by systemd which records much activity.

**journalctl -b** shows you messages from the last boot
**journalctl -b -1** shows you messages from the boot before the last boot.
**journalctl -k -b** shows you kernel log messages from last boot. 
errors may be in red.
see **man journalctl** for many other options.

sudo is not needed for these.


thank you so much!!

---

