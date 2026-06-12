---
title: "manual trim"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by jon12 on 2013-09-19
what is the manual trim command for XUbuntu with xfce   13.04??
for SSD

---

### Post by kanikilu on 2013-09-19
I don't have linux on a computer with an SSD, so I don't know off the top of my head, but a quick search brings this up:

[http://askubuntu.com/questions/18903/how-to-enable-trim](http://askubuntu.com/questions/18903/how-to-enable-trim)

---

### Post by oldfred on 2013-09-20
Make sure BIOS is in AHCI mode for trim to work.

I converted from discard to a cron task. 
Same link in askUbuntu link above.


 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim


 #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

   
running command showed this:
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

---

