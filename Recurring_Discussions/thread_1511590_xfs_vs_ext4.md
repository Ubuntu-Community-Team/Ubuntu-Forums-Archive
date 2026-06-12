---
title: "xfs vs ext4"
date: 2010-06-17
forum: Recurring Discussions
---

### Post by ArcticVanguard on 2010-06-17
Could someone do me a favor and explain the difference between the various file systems, please? What features does xfs have versus ext4? Pretty much all my files are stored on an external USB drive. Would it be worth my time to back up my external drive, reformat to xfs, and then copy the files back over again? I hear xfs is faster, but I don't really know any details. I understand that xfs is a journaling filesystem, which protects the files in the case of a power surge. That shouldn't be a problem for me, since I'm using a laptop with a (working) battery.

My apologies if something I posted didn't make sense, it's late at night, and I'm starting to get tired.

---

### Post by dcstar on 2010-06-17
> **ArcticVanguard said:**
> Could someone do me a favor and explain the difference between the various file systems, please? What features does xfs have versus ext4? Pretty much all my files are stored on an external USB drive. Would it be worth my time to back up my external drive, reformat to xfs, and then copy the files back over again? I hear xfs is faster, but I don't really know any details. I understand that xfs is a journaling filesystem, which protects the files in the case of a power surge. That shouldn't be a problem for me, since I'm using a laptop with a (working) battery.

My apologies if something I posted didn't make sense, it's late at night, and I'm starting to get tired.

EXT3 is journaling, EXT4 is journaling.

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by elliotn on 2010-06-17
I dont know the different but I prefer ext4

---

### Post by ArcticVanguard on 2010-06-17
> **elliotn said:**
> I dont know the different but I prefer ext4

That doesn't help me at all. Why do you prefer it? How can you prefer it if you don't know the difference?

---

### Post by cascade9 on 2010-06-17
> **ArcticVanguard said:**
> Would it be worth my time to back up my external drive, reformat to xfs, and then copy the files back over again? I hear xfs is faster, but I don't really know any details.

Not worth it IMO, and XFS can be faster than EXT4...and it can be slower- 

[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)

---

### Post by dabl on 2010-06-17
Empirical data:

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

Several years ago I installed Kubuntu on an XFS filesystem.  After a couple of months, a large VM began having trouble opening and closing -- went from 60 seconds closing to 3+ minutes.  I re-installed on ext3 at the time, and am presently running Kubuntu on ext4.  That said, I think XFS is probably fine for a data partition, on a server for example.  But I wouldn't recommend it for a root filesystem.

I have run my sidux (64-bit) OS on a JFS filesystem for about a year now.  JFS is native 64-bit, and it seems fast and stable.

That's my two cents' worth on the topic.

---

### Post by ArcticVanguard on 2010-06-17
Cascade, dabl, thank you for the links and assistance. You both answered my questions. Thank you again.

---

### Post by bodhi.zazen on 2010-06-17
I would not use a file system solely on benchmarks, you need to look at the features such as stability, cross platform compatibility, does the file system support ACL ? etc, etc.

[http://www.linux.com/archive/feature/31939](http://www.linux.com/archive/feature/31939)
[http://www.linux.com/articles/31966](http://www.linux.com/articles/31966)

IMO xfs is more vulnerable to power outages then ext4 .

In general I have not seen a large performance difference between the various file systems, but it depends on what you are doing with our disk drives.

If you are interested in trying a new file system, I highly suggest you look at btrfs

[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)
[https://btrfs.wiki.kernel.org/index.php/FAQ](https://btrfs.wiki.kernel.org/index.php/FAQ)

---

### Post by Chris Musampa on 2010-06-17
I have the recordings partition on my mythbox as xfs because I read it performs better with large files than ext3, I don't know if that's still the case with ext4.

---

### Post by srs5694 on 2010-06-17
> **ArcticVanguard said:**
> I understand that xfs is a journaling filesystem, which protects the files in the case of a power surge. That shouldn't be a problem for me, since I'm using a laptop with a (working) battery.

All the major Linux filesystems (ext3fs, ext4fs, ReiserFS, XFS, JFS, and Btrfs) have journals. Ext2fs lacks a journal, as do some non-native filesystems (such as FAT).

Power surges aren't really the issue per se. What a journal does is to keep a record of what parts of the disk are in use at any given moment. Then, after *any* sort of uncontrolled shutdown (a USB drive being disconnected from the computer, a system crash, a power outage, etc.), when the system starts up again, it can check only those parts of the disk that the journal says had been in use. Without a journal, the computer must check the *entire* filesystem, which can take a much longer time. Power surges can cause system crashes, but other than this, they aren't really related to this; and lots of other things can cause the sorts of uncontrolled shutdowns that make journals valuable. Some of these problems can occur on laptops, and might even be more likely on a laptop. For instance, if your battery runs out and the auto-shutdown feature doesn't work or is sluggish, you'll end up with a disk in need of a check when you plug the computer back in.

---

### Post by philinux on 2010-06-17
Moved to Recurring.

---

### Post by mickie.kext on 2010-06-17
XFS does not have any tangible benefit if you are desktop user. Also note that under some circumstances it have stability issues. If you do not have more than 8TB of storage, it is smartest to stick with EXT3 until BTRFS gets stable. BTRFS will rock by the way.

---

