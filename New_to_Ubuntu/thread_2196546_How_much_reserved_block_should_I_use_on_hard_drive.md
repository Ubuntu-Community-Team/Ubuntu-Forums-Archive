---
title: "How much reserved block should I use on hard drives?"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by symphonius on 2013-12-30
So, I'm new to linux, I got a new 1TB HDD and I have no idea how much reserved block I should put. For those who doesn't know what I'm talking about look here: [https://wiki.archlinux.org/index.php/ext4#Remove_reserved_blocks](https://wiki.archlinux.org/index.php/ext4#Remove_reserved_blocks)

I want to set it to 0.5%, but that's only 5GB, is that enough for a 1TB HDD? If I were to use that HDD for torrenting, should I use a higher reserve? If it is only for archiving is it alright to set it lower?

---

### Post by varunendra on 2014-01-02
The reserved blocks, as far as I know, serve two main purposes -

**1)** Keep some space empty to manage fragmentation. With insanely large size of today's files, this purpose isn't solved properly anyway if the non-reserved space gets full.
**2)** More importantly, it keeps some empty space so that even if the non-reserved space gets full and the system crashes because of that, the root has still enough empty space to log in and manage the space/fix issues.

The second point above is, I believe, the main purpose of the concept of keeping reserved blocks and is applicable to only those partitions where files are created while user login and running the system.

As such, I think you should create a separate partition for root (/), and keep the reserved block about 1-2 GB on that partition only. If you prefer multiple partitions like separate / and /home etc., you can follow the same rule for them as well (keep the space 1-2 GB reserved, depending upon their usage and allocated space).

For the data or non-system partitions, the reserved block can be safely set to 0.

Bear in mind that for general maintenance purpose, even 200 MB is sufficient. But some root level operations (like installing packages) may sometimes require about a GB or even more of temporary space to complete smoothly. Any program that is run with root privileges has access to all the space on the drive, and the reserved space is meaningless for it.

As per my personal experience, even 2 GB space in reserved blocks is more than plenty for the purpose it solves. But if you are the kind of user who runs even video rendering programs as 'root', then even 10 GB reserved space (on the system partitions) can be insufficient. ;)

---

### Post by symphonius on 2014-01-02
> **varunendra said:**
> As such, I think you should create a separate partition for root (/), and keep the reserved block about 1-2 GB on that partition only. If you prefer multiple partitions like separate / and /home etc., you can follow the same rule for them as well (keep the space 1-2 GB reserved, depending upon their usage and allocated space).

For the data or non-system partitions, the reserved block can be safely set to 0.


So, the reserved block isn't proportional to the size of the partition?

One last question, when I formatted my 1TB HDD using gparted, it said that 14.18 GiB is used and when I changed the reserved block to just 1% which would be 10 GB, the used space is still 14.18GB, what does this mean?

---

### Post by Impavidus on 2014-01-02
> **jgj.adaoag said:**
> One last question, when I formatted my 1TB HDD using gparted, it said that 14.18 GiB is used and when I changed the reserved block to just 1% which would be 10 GB, the used space is still 14.18GB, what does this mean?The 14.18GB is the filesystem overhead.

---

### Post by varunendra on 2014-01-02
> **jgj.adaoag said:**
> So, the reserved block isn't proportional to the size of the partition?

Yes it is - 5% by default. You'd have to set the percentage in such a way that the reserved space in GB becomes 1-2 GB.

And the 14.18 GB is what Impavidus pointed out - filesystem overhead, which includes partition table, MFTs etc.

---

### Post by chkneater on 2014-01-02
I've used about 150GB for the filesystem (UbuStud13.10), then a 500GB NTFS to store important stuff in case of castophre and also so I can share files with Windonts.  That still leaves 300+ to fool around with...

---

