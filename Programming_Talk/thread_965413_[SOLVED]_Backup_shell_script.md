---
title: "[SOLVED] Backup shell script"
date: 2008-10-31
forum: Programming Talk
---

### Post by king vash on 2008-10-31
I wrote a small little script and installed it to **/etc/cron.weekly** to backup some of my folders from one hard drive to another. The problem is that they other drive is not mounted unless I click on it in my computer.
 
I do not know the command to mount a drive could someone help me.
Below is my script that does the backing up.

#!/bin/sh

percent=$(df | sed -n 's!/dev/sdb1!&!p' | awk '{ print $5}' | cut -d'%' -f1 )


if [ $percent -le "90" ]; then
  cp -r -u -t "/media/disk/" "/home/king/Documents" "/home/king/Games" "/home/king/Music" "/home/king/Pictures" "/home/king/scripts"
  cp -r -u -t "/media/disk/Videos/" "/home/king/Videos/Movies" "/home/king/Videos/Random" "/home/king/Videos/TV shows"
else
  echo "we running out of space to backup files on"
fi

---

### Post by unutbu on 2008-10-31
I think the command you are looking for is
```

mount /dev/sdb1 /media/disk
```
Alternatively, if you post your /etc/fstab, we should be able to configure your machine so that your backup partition is mounted at boot time. (This is assuming that the backup partition is always connected to your machine.)

---

