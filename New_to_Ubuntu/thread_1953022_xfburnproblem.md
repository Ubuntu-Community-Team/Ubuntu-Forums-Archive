---
title: "xfburnproblem"
date: 2012-04-05
forum: New to Ubuntu
---

### Post by rollerworld on 2012-04-05
I cannot get xfburn to burn cd/dvd disks, can you please recommend an alternative program simple to use that works. Thanks.

---

### Post by oklokl on 2012-04-05
new bug...
(New symptoms)
me to..

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076/comments/57](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076/comments/57)
[http://ubuntuforums.org/showthread.php?t=1895338](http://ubuntuforums.org/showthread.php?t=1895338)

sudo apt-get install k3b

sudo sh -c 'echo "@cdrom - memlock unlimited" >> /etc/security/limits.conf'

rebooting..

k3b burning..

---

### Post by Zill on 2012-04-05
> **rollerworld said:**
> I cannot get xfburn to burn cd/dvd disks, can you please recommend an alternative program simple to use that works. Thanks.
[GnomeBaker]("https://help.ubuntu.com/community/GnomeBaker") works for me. :-)

---

### Post by marinara on 2012-04-05
yeah, this week xfburn made a coaster, then made a good disk, and then my DVD-R drive wouldn't eject :(

---

### Post by Peripheral Visionary on 2012-04-05
It's weird. Xfburn is the *only* disk burning software that *always* works on my machine. Brasero always made coasters, and K3B was hit-or-miss. Funny how a lot of things depend so much on your own hardware's "temperament."

---

### Post by andrew.46 on 2012-04-05
This provides as good a time as any to pimp my commandline burning page:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

These commandline have been working for me for years :).

---

### Post by rollerworld on 2012-04-06
> **oklokl said:**
> new bug...
(New symptoms)
me to..

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076/comments/57](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/149076/comments/57)
[http://ubuntuforums.org/showthread.php?t=1895338](http://ubuntuforums.org/showthread.php?t=1895338)

sudo apt-get install k3b

sudo sh -c 'echo "@cdrom - memlock unlimited" >> /etc/security/limits.conf'

rebooting..

k3b burning..

Thanks, k3b worked for me, rollerworld

---

