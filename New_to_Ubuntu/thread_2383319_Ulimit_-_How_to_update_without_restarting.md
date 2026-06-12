---
title: "Ulimit - How to update without restarting?"
date: 2018-01-23
forum: New to Ubuntu
---

### Post by agriz2 on 2018-01-23
```
/etc/security/limits.conf
*         hard    nofile      500000
*         soft    nofile      500000
root      hard    nofile      500000
root      soft    nofile      500000
Ulimit -a is howing the following
 ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 127837
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 127837
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited
Ulimit is still showing only 1024
ulimit -n
1024


ulimit -Hn
1048576
ulimit -Sn
1024
```

How to set ulimit consistently ?

I tried the following.Still no use

```
fs.inotify.max_user_watches = 100000
```

---

### Post by tchambers on 2018-01-24
changes in /etc/security/limits.conf don't require a reboot, but you do need to close all active session windows. Session windows use the values in limits.conf when the session was opened.

log out and log back in and the changes should take effect.

---

