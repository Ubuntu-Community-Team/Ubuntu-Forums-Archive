---
title: "/etc folder is very huge, and storage is filled up 100%"
date: 2015-04-24
forum: New to Ubuntu
---

### Post by aidan7 on 2015-04-24
Hi all,

I have vmware and lamp server installed on it. I realized that my storage is already full and basically i have 2 options to solve the issue:

1. Add additional storage to VM and expand the partitions, I add a 10GB additional storage but then I stuck on how to expand the partitions, as i am not familiar with it, I am afraid i'll screw the whole thing.
```

fdisk -l

Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fad9


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        1567    12331009    5  Extended
/dev/sda3            1959        3916    15727635   83  Linux
/dev/sda4            1567        1958     3145747   8e  Linux LVM
/dev/sda5              32        1567    12331008   8e  Linux LVM
```


My 2'nd option is to find the "garbage" and delete it.

```
df -h


Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/turnkey-root
                         29G   28G     0 100% /
none                  497M  188K  496M   1% /dev
none                  502M     0  502M   0% /dev/shm
none                  502M  296K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda1             228M   20M  196M  10% /boot
```

I know that 19GB is occupied by /etc folder and 8 GB is occupied by /var folder where mysql DB is installed.

I drill down to the /etc folder and found folder /etc/.git/objects is fully used 19GB.

structure of it is 
```
ls /etc/.git/objects
00  07  0e  15  1c  23  2a  31  38  3f  46  4d  54  5b  62  69  70  77  7e  85  8c  93  9a  a1  a8  af  b6  bd  c4  cb  d2  d9  e0  e7  ee  f5  fc
01  08  0f  16  1d  24  2b  32  39  40  47  4e  55  5c  63  6a  71  78  7f  86  8d  94  9b  a2  a9  b0  b7  be  c5  cc  d3  da  e1  e8  ef  f6  fd
02  09  10  17  1e  25  2c  33  3a  41  48  4f  56  5d  64  6b  72  79  80  87  8e  95  9c  a3  aa  b1  b8  bf  c6  cd  d4  db  e2  e9  f0  f7  fe
03  0a  11  18  1f  26  2d  34  3b  42  49  50  57  5e  65  6c  73  7a  81  88  8f  96  9d  a4  ab  b2  b9  c0  c7  ce  d5  dc  e3  ea  f1  f8  ff
04  0b  12  19  20  27  2e  35  3c  43  4a  51  58  5f  66  6d  74  7b  82  89  90  97  9e  a5  ac  b3  ba  c1  c8  cf  d6  dd  e4  eb  f2  f9  info
05  0c  13  1a  21  28  2f  36  3d  44  4b  52  59  60  67  6e  75  7c  83  8a  91  98  9f  a6  ad  b4  bb  c2  c9  d0  d7  de  e5  ec  f3  fa  pack
06  0d  14  1b  22  29  30  37  3e  45  4c  53  5a  61  68  6f  76  7d  84  8b  92  99  a0  a7  ae  b5  bc  c3  ca  d1  d8  df  e6  ed  f4  fb
```



Need your advice on my issue. How to free the space in storage?
Does /etc/.git/objects file is useless?

Thanks.

---

### Post by TheFu on 2015-04-24
Please edit and insert "code tags" for the OP so things line up (Adv Rely). Why keep a .git in /etc at all?  Put it somewhere else or just use daily backups as version control like every sysadmin has done for 40 yrs.

19G in /etc !!!!!! Holy CRAP Batman!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
```
$ du -sh /etc
11M     /etc
```
and on another box
```
$ sudo du -sh /etc
14M     /etc
```

You need to find what is wasting all that storage.  Could you have been hacked?

If you want to add more storage with a 2nd virtual disk - fine. Add the disk, mount it temporarily somewhere, move files over to the storage, then mount it where you want and update the fstab.  It is usually easiest to do this with a liveCD booted, not on a live running OS.

Which VMware are you using? They make like 6 very different VM products.

---

### Post by sandyd on 2015-04-24
> **aidan7 said:**
> Hi all,

I have vmware and lamp server installed on it. I realized that my storage is already full and basically i have 2 options to solve the issue:

1. Add additional storage to VM and expand the partitions, I add a 10GB additional storage but then I stuck on how to expand the partitions, as i am not familiar with it, I am afraid i'll screw the whole thing.




My 2'nd option is to find the "garbage" and delete it.



I know that 19GB is occupied by /etc folder and 8 GB is occupied by /var folder where mysql DB is installed.

I drill down to the /etc folder and found folder /etc/.git/objects is fully used 19GB.

structure of it is 




Need your advice on my issue. How to free the space in storage?
Does /etc/.git/objects file is useless?

Thanks.
Hi, did you install Ubuntu manually, or through an image?

Are you using any git repositories?

Whats the output of```
cd /etc
git log -1
git remote -v
```

---

### Post by TheFu on 2015-04-24
Thanks for trying to do the *code* thing - close, but not quite. There's a button (#) under "adv reply" or you can change whatever tag you used into "code" so things line up. I'm too old to struggle over columns. If the columns don't line, it isn't correct. Thanks.

If you aren''t using git, then wipe everything in /etc/.git - it isn't helping you. If you are using git, then you already know what is in there.

Perhaps using a disk space analyzer would be helpful?  I'd do it with **du -hs /etc/* |sort -rh** - to see which subdirs are sucking all the disk storage, but I'm a shell guy.

---

### Post by aidan7 on 2015-04-24
Hi,
unfortunately i can't answer on both of your questions, as ubuntu was installed long time ago before i join the company.
The outputs:
```

git log -1
commit 1bda468d2b99a31cfcb6540c723de2203ea3d3a3
Author: etckeeper <root@localhost>
Date:   Sat Apr 25 06:25:06 2015 +0800


    daily autocommit

``` 

git -remote -v gives nothing

---

### Post by aidan7 on 2015-04-24
Finally got you :)
Actually each of these 00, 01... are sucking all my space. Each of this file from 80 MB up to 100MB. Except info and pack.
```

ls /etc/.git/objects
00  07  0e  15  1c  23  2a  31  38  3f  46  4d  54  5b  62  69  70  77  7e  85  8c  93  9a  a1  a8  af  b6  bd  c4  cb  d2  d9  e0  e7  ee  f5  fc
01  08  0f  16  1d  24  2b  32  39  40  47  4e  55  5c  63  6a  71  78  7f  86  8d  94  9b  a2  a9  b0  b7  be  c5  cc  d3  da  e1  e8  ef  f6  fd
02  09  10  17  1e  25  2c  33  3a  41  48  4f  56  5d  64  6b  72  79  80  87  8e  95  9c  a3  aa  b1  b8  bf  c6  cd  d4  db  e2  e9  f0  f7  fe
03  0a  11  18  1f  26  2d  34  3b  42  49  50  57  5e  65  6c  73  7a  81  88  8f  96  9d  a4  ab  b2  b9  c0  c7  ce  d5  dc  e3  ea  f1  f8  ff
04  0b  12  19  20  27  2e  35  3c  43  4a  51  58  5f  66  6d  74  7b  82  89  90  97  9e  a5  ac  b3  ba  c1  c8  cf  d6  dd  e4  eb  f2  f9  info
05  0c  13  1a  21  28  2f  36  3d  44  4b  52  59  60  67  6e  75  7c  83  8a  91  98  9f  a6  ad  b4  bb  c2  c9  d0  d7  de  e5  ec  f3  fa  pack
06  0d  14  1b  22  29  30  37  3e  45  4c  53  5a  61  68  6f  76  7d  84  8b  92  99  a0  a7  ae  b5  bc  c3  ca  d1  d8  df  e6  ed  f4  fb

```

---

### Post by sandyd on 2015-04-24
Your company is using something called [etckeeper]("http://etckeeper.branchable.com/").

This is now more of a company issue, as the .git directory is part of etckeeper. If you remove the .git directory, you will break etckeeper as they are using Git for version management.

That being said, the most likely possibility is that in the past, someone added huge file(s) to /etc and etckeeper archived it before the files were deleted. If your sure that you can modify etckeeper, take a backup and try [https://rtyley.github.io/bfg-repo-cleaner/](https://rtyley.github.io/bfg-repo-cleaner/)

---

### Post by TheFu on 2015-04-25
[http://www.turnkeylinux.org/forum/support/20111111/etckeeper-has-huge-git-repo-how-remove](http://www.turnkeylinux.org/forum/support/20111111/etckeeper-has-huge-git-repo-how-remove) says you need to run a garbage collection task as root.

# cd /etc
# git gc 

Definitely read the link to understand more.

---

### Post by aidan7 on 2015-04-25
Thank you very much guys!!!
The command git gc was my solution, it cleaned up all 19GB of garbage and my system back to normal.
```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/turnkey-root
                       29G  8.6G   19G  32% /
none                  497M  188K  496M   1% /dev
none                  502M     0  502M   0% /dev/shm
none                  502M  296K  501M   1% /var/run
none                  502M     0  502M   0% /var/lock
none                  502M     0  502M   0% /lib/init/rw
/dev/sda1             228M   20M  196M  10% /boot

```

---

