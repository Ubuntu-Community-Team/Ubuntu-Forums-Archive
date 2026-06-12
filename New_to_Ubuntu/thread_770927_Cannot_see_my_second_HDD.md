---
title: "Cannot see my second HDD"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by mecanologo on 2008-04-27
Hey all!
My computer has two 120 gigs HDD. (Not partitions).
I installed Ubuntu on my secondary HDD from Windows, and both boot greatly!
On my Computer I can see three drives which are:
[LIST]
[*]CD/HDDVD Drive
[*]Main HDD (Which is my Vista drive I may easily explore)
[*]Toshiba System Volume (Has some files I ignore)
[*]Filesystem (Here's my Linux)
[/LIST]
sooo, my question, is how can I access the rest of the information on this drive? I love my Ubuntu, and Vista takes too long on booting... I prefer to use this baby!, Yet, I do need to access such drive.
Thanks.

---

### Post by TeoBigusGeekus on 2008-04-27
Could you please be a bit more specific?
You can't see your vista volume from ubuntu - is this your question?

---

### Post by mecanologo on 2008-04-27
Nope. I CAN see my vista drive.
NP there. 
Ubuntu is on my second drive, and I may not read the rest of the second drive.
Thanks

---

### Post by TeoBigusGeekus on 2008-04-27
I still don't understand... (sorry it's Easter in Greece and I've drunk a lot of wine today).
So you want to make Ubuntu see your whole second drive?
You want vista to see your whole second drive?
What is your case?

---

### Post by mecanologo on 2008-04-27
Vista's fine. (I actually don't care much of it, thou)
I want to be able to read more than my Ubuntu from the second HDD. (When logged in at Ubuntu)
Thanks

---

### Post by TeoBigusGeekus on 2008-04-27
Right oh!!!
Open a terminal in Ubuntu and type
```
sudo fdisk -l
```
that's -L and post the contents.

---

### Post by mecanologo on 2008-04-27
jose@jose-laptop:~$ sudo fdisk -l
[sudo] password for jose: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fb778d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       14594   115683328    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117219328    f  W95 Ext'd (LBA)
/dev/sdb5               1       14594   117218304    7  HPFS/NTFS
jose@jose-laptop:~$

---

### Post by TeoBigusGeekus on 2008-04-27
> **mecanologo said:**
> 

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117219328    f  W95 Ext'd (LBA)
/dev/sdb5               1       14594   117218304    7  HPFS/NTFS
jose@jose-laptop:~$

As you can see, Ubuntu recognises all 120gigs of your 2nd hd, so you shouldn't have a problem...
When you go to system monitor, how much free space does ubuntu give you for your 2nd volume?

---

### Post by mecanologo on 2008-04-27
That's it!

---

### Post by TeoBigusGeekus on 2008-04-27
Would you be king enough to explain each entry?

---

### Post by mecanologo on 2008-04-27
That's my little problem....
LOL

---

