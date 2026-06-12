---
title: "Need someone help please."
date: 2013-03-09
forum: New to Ubuntu
---

### Post by manid111 on 2013-03-09
Recently got installed Ubuntu12.10  with  WindowsXP, but now problem is '/ '  size only showing free size is 4.5Mb. Can somebody help me to rectify this problem, advancely thanks.      root@mani-desktop:~# df -h Filesystem       Size    Used   Avail   Use%   Mounted on /dev/sdb5       3.3G    3.1G    4.5M   100%      / udev                 996M   4.0K    996M   1%        /dev tmpfs              402M   804K   401M    1%       /run none                5.0M     0  5.       0M      0%      /run/lock none             1004M  1000K  1003M   1%     /run/shm none              100M     60K     100M    1%     /run/user /dev/sdb3    120G     92G      28G     77%   /media/mani/F4C083E0C083A786 /dev/sdb1      14G     9.1G    5.0G    65%     /media/mani/C23054EA3054E747

---

### Post by ptn107 on 2013-03-09
Why is your root partition only 3.3 G.  When you installed you didn't make the partition big enough.  A typical Ubuntu install on / uses about 4G not including files in your home folder.  You need to run Ubuntu from a live cd and use Gparted to resize the root partition /dev/sdb5.

---

### Post by Old_Grey_Wolf on 2013-03-09
While ptn107 was replying, I converted the output of the of the df -h command to something a little more readable.
```
Filesystem        Size Used Avail Use% Mounted on 
/dev/sdb5         3.3G 3.1G 4.5M  100% / 
udev              996M 4.0K 996M    1% /dev 
tmpfs             402M 804K 401M    1% /run 
none              5.0M 0 5.   0M    0% /run/lock 
none             1004M 1000K 1003M  1% /run/shm 
none              100M 60K  100M    1% /run/user 
/dev/sdb3         120G 92G   28G   77% /media/mani/F4C083E0C083A786 
/dev/sdb1          14G 9.1G 5.0G   65% /media/mani/C23054EA3054E747
```
As ptn107 said, root was only given 3.3G.

---

