---
title: "Formating a drive"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-02-24
Hello all
Had to up-grade my 2nd hard drive, "or as I think of it my main storage one", up from a 160gb to 2TB, first time I tried to format it via Ubuntu here but got 4 - 5 error messages, as I needed it to be a NFTS "microdoze" format, I ended up using my xp DVD

7hrs to format a 2TB drive, ? with 2 1/2 hrs to move 105 000 files "131gb"   does that sound about right.

Oh, the new drive is a Hitachi Coolspin 5K3000 2TB SATA 3.5, its suppose to be 6gb per second, er NO it's loading at 14.3 mb per second but it is coming from an old IDE drive

Dave[SIZE=1][/SIZE]

---

### Post by ajgreeny on 2012-02-24
> **DaveMcC said:**
> Hello all
Had to up-grade my 2nd hard drive, "or as I think of it my main storage one", up from a 160gb to 2TB, first time I tried to format it via Ubuntu here but got 4 - 5 error messages, as I needed it to be a NFTS "microdoze" format, I ended up using my xp DVD

7hrs to format a 2TB drive, ? with 2 1/2 hrs to move 105 000 files "131gb"   does that sound about right.

Oh, the new drive is a Hitachi Coolspin 5K3000 2TB SATA 3.5, its suppose to be 6gb per second, er NO it's loading at 14.3 mb per second but it is coming from an old IDE drive

Dave
Sorry, but I don't quite understand what you actually did to copy the partition from disk to disk.  What did you use to do it; gparted?  You can certainly make an ntfs partition using gparted without a problem.

More information please.
Also read about [clonezilla]("http://clonezilla.org/") which would probably have done the whole clone/restore job a lot quicker.

---

### Post by HeroOfCanton on 2012-02-24
7 hours to format sounds extreme. 2 1/2 hours to copy 105K files taking up 131GB does not.

Remember you are limited by the weakest link in the chain. You can't copy any faster than the old drive can transfer. Moving a high number of files like that will weigh heavily on your system.

I would be a little concerned over a 7 hour standard format for 2 TB. Maybe a low level format, but I don't think that's what you were doing. Doesn't sound right at all. Try a performance test and see if it's matching what you would expect. [https://help.ubuntu.com/11.10/ubuntu-help/disk-benchmark.html](https://help.ubuntu.com/11.10/ubuntu-help/disk-benchmark.html)

---

### Post by quadproc on 2012-02-24
> **DaveMcC said:**
> 
7hrs to format a 2TB drive, ? with 2 1/2 hrs to move 105 000 files "131gb"   does that sound about right.

You didn't say which filesystems you used on the new drive.  Generally, older file systems tend to run out of gas above 1 TB; many of the utility programs cannot correctly deal with a 2 TB size.  You might wish to partition the drive into two or more pieces so that each piece is 1 TB or less.

The biggest formats that I have ever done have been about 100 GB and those only took a few minutes at most.  It does sound like something is amiss.  Partitioning does take a while on my system which uses 1 TB disks, perhaps 1/2 hour, but most of that time seems to be used in moving things from one partition to another.

quadproc

---

### Post by audiomick on 2012-02-24
I put a 2TB drive into my machine a couple of months back. I formatted it to four ext4 partitions at about 500GB each. I don't remember exactly how long it took, but am sure it was well under an hour.

---

