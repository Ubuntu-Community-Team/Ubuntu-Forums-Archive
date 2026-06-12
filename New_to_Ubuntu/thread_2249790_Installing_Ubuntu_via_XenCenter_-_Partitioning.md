---
title: "Installing Ubuntu via XenCenter - Partitioning"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by halimzhz on 2014-10-24
Dear All,

I'm a newbie with Ubuntu, currently i'm trying to install latest Ubuntu on my Xenserver via Xencenter, i just follow this link [http://virantha.com/2014/05/21/ubuntu-14-04-trusty-on-xenserver-62/](http://virantha.com/2014/05/21/ubuntu-14-04-trusty-on-xenserver-62/) for latest Ubuntu, but the problem now is on Partitining Disk, based on my application script, the requirment for disk partition is like below:

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root
                       20G   14G  4.8G  74% /
tmpfs                 751M     0  751M   0% /lib/init/rw
udev                  737M   76K  737M   1% /dev
tmpfs                 751M     0  751M   0% /dev/shm
/dev/xvda1            228M   16M  201M   8% /boot

The size as above is not important, and i'm now at Xencenter on menu of '[!!] Partition disks', i understand i have to select 'Manual' but seriously what suppose on next page?

Please help me on the right step to make the partition as above. TQ

---

