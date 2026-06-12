---
title: "[SOLVED] Where did my available space go"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-08-20
My Ubuntu partition has 27.1 GB, with 15.4 free and 14.0 available.
I can only account for about 4 GB of data on this partition.
Where did my available space go, more important, how do I get it back

---

### Post by Vivaldi Gloria on 2008-08-20
Press ALT + F2 and start

```
baobab
```

Scan the filesystem to find out what's going on.

---

### Post by Shazaam on 2008-08-20
Did you use "Disk Usage Analyzer" to get that info?
If you did, open it again, go to Edit>Preferences and uncheck "gvfs-fuse-daemon". Rerun DUA.

---

### Post by C.S.Cameron on 2008-08-20
I will try to install Disk Usage Analyzer,
I was using system manager to check available space and checking folder sizes with File Browser for folders that have anything over 10 GB in them

---

### Post by Shazaam on 2008-08-20
Disk Usage Analyzer is installed by default.
It's on your panel at Applications>Accessories>Disk Usage Analyzer

---

### Post by Gregmond on 2008-08-20
what springs to mind is:

use Ctrl + h to ensure you are viewing hidden files.
Have you emptied the trash ?

I have found that the trashcan doesn't always delete everything and you sometimes have to go into the hidden folder and delete everything manually.

---

### Post by Vivaldi Gloria on 2008-08-20
> **C.S.Cameron said:**
> I will try to install Disk Usage Analyzer,

I told you how to start it, the next post told you another way to start it. Read more carefully.

---

### Post by C.S.Cameron on 2008-08-20
Vivaldi:
Yes I tried it and understood Shazaam.
After un-checking "gvfs-fuse-daemon" and restarting DUA I find:
Total... 27.1, Used 11.7, Available 15.4.
But the list below doesn't add up to anything like 11.7 GB.
I wonder I it could have anything to do with several un-successful tries copying my wifes 15 GB home folder to the disk?
Trash has a file that I can't git rid of.

---

### Post by jmate24 on 2008-08-20
that is because Ubuntu needs at least 4-6GB of free disk space to opperate.

---

### Post by Vivaldi Gloria on 2008-08-20
Can you post the output of the commands

```
sudo fdisk -l
df -h
sudo du -sh 
```

Please use code tags (#) when you do. I find it very hard to read otherwise.

---

### Post by C.S.Cameron on 2008-08-21
```
cscameron@cscameron-mITX:~$ sudo fdisk -l
[sudo] password for cscameron:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000b99d


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10872    87329308+   7  HPFS/NTFS
/dev/sda2           10873       14593    29888932+   5  Extended
/dev/sda5           10873       14434    28611733+  83  Linux
/dev/sda6           14435       14593     1277136   82  Linux swap / Solaris
cscameron@cscameron-mITX:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              28G   12G   15G  46% /
varrun               1009M  112K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   40K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
lrm                  1009M   39M  970M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       28G   12G   15G  46% /home/cscameron/.gvfs
cscameron@cscameron-mITX:~$ sudo du -sh
du: cannot access `./.gvfs': Permission denied
561M    .
```

---

### Post by drs305 on 2008-08-21
It could be unemptied trash. I just presented a solution in another post if that is the problem:
[root directory (sda2) full]("http://ubuntuforums.org/showthread.php?t=896498#4")

---

### Post by Vivaldi Gloria on 2008-08-21
Oops. The last command should read:

```
sudo du -sh /*
```

Also

> **C.S.Cameron said:**
> My Ubuntu partition has 27.1 GB, with 15.4 free and 14.0 available.

How did you find this out?

> restarting DUA I find:
Total... 27.1, Used 11.7, Available 15.4.

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              28G   12G   15G  46% /

They seem to be in agreement.

---

### Post by C.S.Cameron on 2008-08-21
Thanks drs305
Found and deleted the trash and now have 24.2 GB free.

---

