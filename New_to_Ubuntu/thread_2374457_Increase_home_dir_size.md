---
title: "Increase \home dir size"
date: 2017-10-16
forum: New to Ubuntu
---

### Post by forcefire on 2017-10-16
Hi

I have Ubuntu 14.04 installed on a VPS, the /home is too small for 1 program I want to install/run as its needs 3TB of space to store content, how can I take drive space from /STORAGE without reinstalling the VPS, how can I do it without affecting anything stored on the VPS???

Currently the df shows

```
root@******:~# df
Filesystem       1K-blocks       Used  Available Use% Mounted on
/dev/root         50258116    1545132   46136936   4% /
devtmpfs           8201568          4    8201564   1% /dev
none                     4          0          4   0% /sys/fs/cgroup
none               1640424        644    1639780   1% /run
none                  5120          0       5120   0% /run/lock
none               8202100          0    8202100   0% /run/shm
none                102400          0     102400   0% /run/user
/dev/md3         100655024     339688   95179236   1% /home
/dev/md5       11474610520 3768573744 7127726760  35% /STORAGE
```

Cheers

---

### Post by mcparty2 on 2017-10-17
There are several possible ways to achieve this but first of all it make me wonder what program is it that needs installing in the Home directory? Does the program give an option of where you'd like it to store the files?
If it is a user that needs the storage space you can change their home directory to /STORAGE using usermod.

```
usermod -m -d /STORAGE/ username
```

You can check this worked by:

```
cat /etc/passwd | grep username
```

Normally, i'd recommend using LVM to dynamically expand your directories but i fear this would require a re-installation and resetting your partitions (which you wish to avoid) The Ubuntu installation process offers it by default for the root filesystem, though  you may not get the options with some VPS providers. Though, I'd perhaps reconsider it if you are expecting to breach 3TB of data in the future.

I hope this helps

---

