---
title: "Tons of General Problems"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by FlyinMunky40 on 2012-04-06
I have been having many problems with Linux. When installing Linux on an external hard drive, it initially worked, then when I ran the "Install Ubuntu 11.10" It ended up overwriting my C:/ Windows drive. Now the external hard drive no longer has Linux on it, and my C:/ drive no longer has Windows on it. For one, can I retrieve Windows files. For two, how do I expand the size of my Ubuntu partition (I think that is the right word). If anyone could help me solve, or even just understand these problems, it would defiantly be amazing.

I also have a few more problems, but these are the top priorities.

---

### Post by bodhi.zazen on 2012-04-06
You resize partitions with a live CD using gparted.

In terms of your windows data, if it was over written it may be lost.

You can try recovering data from a live CD 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Gone fishing on 2012-04-07
I find it hard to see why it used the Windows partition unless you told it to. I suppose it is possible that you have a messed up partition table, if this is the case you probably don't have any recognizable file system on the drives.

This can probably be fixed with Test disk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) you can get a copy of test disk on the parted magic [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php) live cd

---

### Post by FlyinMunky40 on 2012-04-07
Rather than using a live cd, would it be possible to do this with an external hard drive that has gparted on it?

---

### Post by 2F4U on 2012-04-07
If there is a Linux distribution installed on this drive and if you can boot from it, it should also work.

---

### Post by Mark Phelps on 2012-04-07
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by bodhi.zazen on 2012-04-07
> **FlyinMunky40 said:**
> Rather than using a live cd, would it be possible to do this with an external hard drive that has gparted on it?

It is possible, but impractacle. IMO you should manage paritions with a live CD.

If you are concerned with data recovery, you need to stop using the hard drive ASAP. The longer you run from your hard drive , the greater the data loss as more and more information gets over written. Once the data is over written you can not recover it.

I suggest you read the data recovery page I linked to you.

---

