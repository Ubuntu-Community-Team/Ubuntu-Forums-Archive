---
title: "Not enough free disk space"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by darko6 on 2015-01-31
Hi, i am having the similar problem. Here is my output of '[COLOR=#000000]df -h'[/COLOR] command:

```
darko@darko:~$ df -h
df: ‘/run/user/1001/gvfs’: Permission denied
df: ‘/root/.gvfs’: Permission denied
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  143G   53G   84G  39% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         1,9G  4,0K  1,9G   1% /dev
tmpfs                        389M  1,3M  388M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         1,9G   72M  1,9G   4% /run/shm
none                         100M  216K  100M   1% /run/user
/dev/sda1                    236M  152M   72M  68% /boot
```

---

### Post by lisati on 2015-01-31
*Moved to own thread from [http://ubuntuforums.org/showthread.php?t=2224768](http://ubuntuforums.org/showthread.php?t=2224768)*

---

### Post by Impavidus on 2015-01-31
Then try the same solution as everyone else: uninstall some old kernels.```
sudo apt-get autoremove --purge
```usually does the trick.

---

### Post by oldos2er on 2015-01-31
Why such a small /boot partition?

---

