---
title: "backup manager"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Lylex11 on 2008-05-12
Hi, I installed backup manager and set archive folder to /media/sda4. When I activated backup-manager I forgot to mount /media/sda4 first. I now have a MASSIVE archive somewhere (15Gig or so), but I can't find it. I've searched for it everywhere. Baobab (Disk Usage Analyser) reports I have 15.8GB files, but says I have used 33.0GB of space - I'm guessing that's my system+home files plus the missing (hidden) backup archive. But baobab doesn't show where the archive is. Can anyone help me delete the archive files? I currently have 1.8Gig free space and want more!

Oh, here is what "df -a" gives me...
lylex11:~$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             38441132  34551340   1937092  95% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                  510056        88    509968   1% /var/run
varlock                 510056         0    510056   0% /var/lock
udev                    510056        72    509984   1% /dev
devshm                  510056         0    510056   0% /dev/shm
devpts                       0         0         0   -  /dev/pts
lrm                     510056     35120    474936   7% /lib/modules/2.6.22-14-rt/volatile
/dev/sda1                48052         0     48052   0% /media/sda1
securityfs                   0         0         0   -  /sys/kernel/security

as you can see, 95% HD used (I have a 40GB partition), but I can only find 15.8GB in nautilus or Baobab.

If you can help... Thanks so much

---

### Post by OliverKurz on 2008-06-10
Hi,
in case some partition is mounted now over /media/sda4, the content of the directory '/media/sda4' on the '/' partition is hidden.
Therefore it might help to unmount /media/sda4 ('sudo umount /media/sda4') and delete the contents of the mountpoint manually (if you can find the backup archive there).
Anyway, Baobab should be able to tell you, but maybe not for all directories if entries are hidden or not accessible by your user account.

---

### Post by hyper_ch on 2008-06-10
```

find -size +10G

```

that should output all files bigger than 10GB

---

### Post by Lylex11 on 2008-06-12
Thanks OliverKurz for the above tips. The mount point "/" was indeed hidden. Very helpful. I've managed to delete the hidden backups. Thanks!

---

