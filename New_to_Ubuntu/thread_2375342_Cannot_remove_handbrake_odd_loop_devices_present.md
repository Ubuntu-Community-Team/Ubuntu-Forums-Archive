---
title: "Cannot remove handbrake odd loop devices present"
date: 2017-10-23
forum: New to Ubuntu
---

### Post by bulgin on 2017-10-23
Linux version 4.4.0-97-generic (buildd@lcy01-33) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4) ) #120-Ubuntu SMP Tue Sep 19 17:28:18 UTC 2017

When I view System Monitor I see:

/dev/loop2    /snap/handbr  sqaushfs 91.2 MB   100%
/dev/loop4    /snap/handbr  sqaushfs 91.2 MB   100%

handbrake does not show up in the synaptic package manager yet there is a handbrake desktop icon that I cannot remove.

Additionally the following commands show errors:

 sudo snap find handbrake
[sudo] password for dj: 
sudo: snap: command not found
dj@place:~$ sudo snap remove handbrake
sudo: snap: command not found

Very odd that "snap: command not found"

Mount shows:

/var/lib/snapd/snaps/handbrake-jz_11.snap on /snap/handbrake-jz/11 type squashfs (ro,nodev,relatime)
/var/lib/snapd/snaps/handbrake-jz_12.snap on /snap/handbrake-jz/12 type squashfs (ro,nodev,relatime)

I want to get rid of the handbrake entries and icon.

---

### Post by mc4man on 2017-10-24
Maybe you removed the snapd package

---

