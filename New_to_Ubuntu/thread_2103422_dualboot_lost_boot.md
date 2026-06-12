---
title: "dualboot lost boot"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by afubu2012 on 2013-01-10
Hi!

After installing ubuntu next to win xp, rebooted to ubuntu which I belive messed up windows boot order.

Now I'm unable to boot.. recovery usb did not find grub nor fix it.. here's the report: 

 [http://paste2.org/p/2721623](http://paste2.org/p/2721623)

Cheers!

---

### Post by oldfred on 2013-01-10
Welcome to the forums.

I do not see either Windows nor Ubuntu. And it looks like partition table is totally messed up or has random data. Did you have something unusual installed or abnormal shutdown during install?

```
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1     ?     6,579,571 1,924,427,647 1,917,848,077  12 Compaq diagnostics
/dev/sda2     ? 1,953,251,627 3,771,827,541 1,818,575,915  43 Unknown
/dev/sda3     ?   225,735,265   225,735,274            10  72 Unknown
/dev/sda4       2,642,411,520 2,642,463,409        51,890   0 Empty

```

I might try testdisk first to see if it can find old partitions.  It may find multiple versions of old partitions and you have to select a set that matches starts & ends.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
            Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

