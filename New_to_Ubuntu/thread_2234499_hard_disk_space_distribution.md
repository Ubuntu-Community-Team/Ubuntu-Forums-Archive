---
title: "hard disk space distribution"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by michael191 on 2014-07-15
hi,
i am quite new to ubuntu. i am using lubuntu on an asus laptop and i am thinking of leaving windows for private use although i have to use windows in my daily work.

i have setup lubuntu myself and i have problems with hard disk space distribution, i have 3 user accounts on my laptop (one for administration, 2 for daily use) and i have realized, that my user accounts can only use 7,6 GB hard disk space, although it's a 500 GB HD on the computer. in fact i can see with command "Drives" ("Laufwerke") that there are 5 partitions on my HD with one of them covering 475 GB and just containig "FreeDOS" which was deleivered with the pc.

how can i change the partition sizes so that i do not lose FreeDOS and i have room enough for my user accoúnts?

michael

---

### Post by sudodus on 2014-07-15
Welcome to the Ubuntu Forums :-)

You can use ***gparted*** to edit partitions for example change the size of partitions. If you intend to remove Windows or don't have it at all in this computer at home, it might even be easier to start from the beginning, create a fresh partition table and making an installation of Lubuntu. Freedos is free and can be uploaded to be installed like you upload and install linux.

You should run gparted when booted from another drive, for example the Lubuntu install drive.

Anyway, it would make it easier to give relevant help, if you ***attach a screenshot of gparted showing the drive to a reply***. Go advanced, (red button below the editing window) and click Manage Attachments further down the page. Use the second window and upload the picture. This way there will be a thumbnail, and it will be convenient for people with slow internet (compared to a full picture inline (in the reply post).

---

