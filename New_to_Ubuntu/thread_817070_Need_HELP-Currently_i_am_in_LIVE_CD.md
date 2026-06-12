---
title: "Need HELP-Currently i am in LIVE CD"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-03
```
Currently i am inside live CD.

I want to back up my UBUNTU partition.


```

I just want to back up my ubuntu partition using partimage.
I am inside live cd.
I have 4 GB of data in my ubuntu drive.
When i specify any drive i during back up my image is stored inside /home/ubuntu.

But the free space inside that is very small  [Approx 200Mb].

I have two hard disks and my fdisk -l result is

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbedebede

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       19456   130680742+   f  W95 Ext'd (LBA)
/dev/sda5            3188       11091    63488848+   7  HPFS/NTFS
/dev/sda6           11092       19456    67191831    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f5d4ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       13057   104872320    f  W95 Ext'd (LBA)
/dev/sdb2   *       13058       16708    29326657+   7  HPFS/NTFS
/dev/sdb3           16709       19457    22081342+  83  Linux
/dev/sdb5               2        6529    52436128+   7  HPFS/NTFS
/dev/sdb6            6530       13057    52436128+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```

i can save that back up in any partition of my disk.

could any one help me.

---

### Post by rraj.be on 2008-06-03
Any one there.

---

### Post by Sef on 2008-06-03
Wait at least 24 hours before bumping your thread.  Otherwise you could get an infraction for it.  Help will come, but it may take some time.  Everyone here is a volunteer.

---

### Post by rraj.be on 2008-06-03
I am sorry.

I know all of our community members are volunters.

But iam striking my head for last one hour to solve this problem and i am bein inside live cd for more than 2 hours.

i am extremlly sorry if i annoyed have you.

---

### Post by hyper_ch on 2008-06-03
it is also adviced to use a descriptive thread title and not a generic "noob here" or "need help".

---

### Post by rraj.be on 2008-06-03
sure.

---

### Post by louieb on 2008-06-03
Which live CD? Don't think the Ubuntu live CD has partimage.
But anyway
1st you have to make a directory to mount your backup partition.  ```
sudo mkdir /z  
```
2nd you mount your backup partition ```
sudo mount -t ntfs-3g  /dev/sda6 /z 
```
then you run partimage in the destination fiield you put where you want to back it up to. ```
/z/whateverbackup 
```
the psychocats link in signature has a partimage how to.
Good luck.

---

### Post by rraj.be on 2008-06-03
But my problem is my root partition has only 200MiB of free space and so i cant backup my 2GiB backup file.

Is there any way to do that.

---

### Post by louieb on 2008-06-03
I saw only one Linux partition in the  fdisk you posted.  Are you try to create the backup inside the partition your want to back up?  Don't think that going to work with p**artimage**.  **tar **will do that  if you have enough free space. You say you don't have enough room so you can't use **tar** either.
> i can save that back up in any partition of my disk.
Find another partition with enough free space, mount it and use it.

---

### Post by rraj.be on 2008-06-03
yes .

I know we cant work with any mounted partition in partimage.

But even if i specify any location to save my backup, its  saving only in 

/home/ubuntu 

i used /media/disk-6 

in destination path.

What should i use.

---

### Post by louieb on 2008-06-04
> **rraj.be said:**
> i used /media/disk-6 in destination path.

That is probably an invalid destination. Surprised it did anything.  Did you try to mount a partition on /media and save your backup in file named disk-6? Thats what you told it to use. 
Did you read the psychocats   partimage tutorial? 

>  What should i use.Can't answer that. Don't know what partition you want to mount and use for your backup. Please explain in detail what you are trying to do and what you have done. Then I probably can figure out what you a doing wrong.    You have to do the 2 steps I described in post #7 before running partimage. 

As an option try [Clonezilla]("http://www.clonezilla.org/"). it has a front end to partimage thats easy to use.

---

### Post by rraj.be on 2008-06-04
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbedebede

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188       19456   130680742+   f  W95 Ext'd (LBA)
/dev/sda5            3188       11091    63488848+   7  HPFS/NTFS
/dev/sda6           11092       19456    67191831    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f5d4ba8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       13057   104872320    f  W95 Ext'd (LBA)
/dev/sdb2   *       13058       16708    29326657+   7  HPFS/NTFS
/dev/sdb3           16709       19457    22081342+  83  Linux
/dev/sdb5               2        6529    52436128+   7  HPFS/NTFS
/dev/sdb6            6530       13057    52436128+   7  HPFS/NTFS
ubuntu@ubuntu:~$
```

i want to back up my sdb3.

want to store in any other partition.


i used /media/disk-6 because in my explorer it displayed the path as that.

---

