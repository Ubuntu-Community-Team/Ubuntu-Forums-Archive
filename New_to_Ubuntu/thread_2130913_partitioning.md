---
title: "partitioning"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by edenriot on 2013-03-30
I have selected "Install Ubuntu alongside Windows XP" I have selected the amount I want partitioned and I have clicked the "Install Now" button.  A message box has come up saying "Before you can select a new partition size, any previous changes have to be written to disk.  You cannot undo this operations.  Please note that the resize operation may take a long time."  I have the choice between clicking "Go Back" or "Continue" and neither of those options seems to do anything."  What needs to be done?  And please, for the sake of all that is holy, respond with the simplest explanation that you can.

---

### Post by Bashing-om on 2013-03-30
edenriot;
Standard partition = 4 partitions max. Windows may have used all 4 ? Do all partitioning in windows to make room for ubuntu, Leave that made partition unformatted, install ubuntu along side of.
[INDENT=3]
hth

[/INDENT]

---

### Post by edenriot on 2013-03-30
Thanks!  I understand the problem now!  Although I still don't know how to fix it.  I know this is a Ubuntu forum but do you have any idea where I go to change partition setttings in Windows?

---

### Post by Bashing-om on 2013-03-30
edenriot;

It is not determined at this time what the partitioning scheme is. If it is an older machine it is what is termed as msdos (MBR),
In this instance and IF windows is using up all 4 partitions, one of which is the recovery partition, many have copied that to a dvd and in Windows set that partition as unallocated space. The recommendation is after redoing the partitions to run Windows check disk twice and twice defrag. As you are not familiar with the procedure, do your home work -> search this forum for Mark phelps
and oldfred threads in this respect. Both are very knowledgeable and have given excellent advise. I do not do windows.

One should by all means boot up the install medium and "try ubuntu" mode and verify all devices work. In this mode, one may look at the disk and see its partitioning scheme.
Terminal codes:
```
sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
```
If you have any doubts about the output, by all means post the output here for our examination and advisement.[INDENT=3]
I do make an effort to help

[/INDENT]

---

