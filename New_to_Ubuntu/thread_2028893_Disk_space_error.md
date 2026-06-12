---
title: "Disk space error"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by chakri1 on 2012-07-19
Hello,

I am trying to find out available disk space in my Desktop. Here are the commands that I tried and their outputs :

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              74G   57G   14G  81% /
none                  2.0G  688K  2.0G   1% /dev
none                  2.0G  1.6M  2.0G   1% /dev/shm
none                  2.0G  260K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda1             184M   31M  145M  18% /boot
/dev/sda6              66G   19G   45G  30% /home

$ sudo du -hs /
47G	/

First command 'df' shows that 57G is used in '/' partition. Second command 'du' shows 47G is used in '/' folder. I could not understand why '/' partition is using more disk space than '/' folder ?

Any help in understanding how disk space is measured in linux will be much appreciated.

Thanks in advance,
Chak

---

### Post by mmehboobhan on 2012-07-19
Hi

First of all enter this for "du " 
$ cd /
and then following command.

$ du  --si  -s

du: cannot access `./home/sysadmin/.gvfs': Permission denied
6.7 G

Then "df"

$ df --total -ah

Filesystem        Size  Used Avail Use% Mounted on
/dev/sda1          14G  5.4G  7.8G  41% /
udev              1.5G  4.0K  1.5G   1% /dev
devpts               0     0     0    - /dev/pts
tmpfs             601M  1.1M  600M   1% /run
none              5.0M     0  5.0M   0% /run/lock
none              1.5G  156K  1.5G   1% /run/shm
/dev/sda6          56G  1.3G   51G   3% /home
gvfs-fuse-daemon  0.0K  0.0K  0.0K    - /home/sysadmin/.gvfs
total              73G  6.6G   63G  10%

Reason of showing less at du.

  df shows the result in 1000 for 1kb by default and du in 1024 by default. So use --si with du it will show you exat as by df.

I think it will be informative for you.

Thank You

---

### Post by chakri1 on 2012-07-19
Thanks for pointing out difference between du and df. I tried as you suggested and here are the outputs. Still there is some difference between the two outputs.

$ cd /
$ sudo du --si -s
50G	.

$ df --total -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              74G   57G   14G  81% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
fusectl                  0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  2.0G  688K  2.0G   1% /dev
none                     0     0     0   -  /dev/pts
none                  2.0G  1.6M  2.0G   1% /dev/shm
none                  2.0G  260K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sda1             184M   31M  145M  18% /boot
/dev/sda6              66G   19G   45G  30% /home
none                  0.0K  0.0K  0.0K   -  /proc/fs/vmblock/mountPoint
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
gvfs-fuse-daemon         0     0     0   -  /home/chakravarthy/.gvfs
total                 148G   75G   66G  54%

'du' shows 50G and 'df' 57G.

Any idea why this is happening ?

Thanks
Chak

---

