---
title: "File System for archiving data"
date: 2015-09-24
forum: New to Ubuntu
---

### Post by buntunoob2 on 2015-09-24
Hey everybody,

for my data I currently use NTFS. 4 HDDs, 1 large enough to backup the other 3.
As I do manual sync, this requires a lot of time and regular syncing. With 2 copys and NTFS I also have basically no protection towards silent data corruption.
(Even though I do a manual "scrubbing" every time by comparing the contents with my sync tool)

The question is: how can I do better? I think about using a non-Windows FS loosing the compatibility in order to gain better data protection - so what is the right choice for a file system?

I read about BtrFS, advertising "Mostly self-healing in some configurations" (Wikipedia) and "Online data scrubbing for finding errors and automatically fixing them for files with redundant copies" - I could not find out in detail, what "redundant copy" is, but to me it seems somewhat like a Software-RAID.
Looking at ZFS, the intention seems to be the same (checksum and scrubbing)
from my Research, the FS using checksums at all are BtrFS, ZFS, Reiser4, ReFS, NILFS , GPFS and Reliance (Nitro/Edge).
Most of them are discontinued, cost money or are designed for much larger-scale systems.

I don't want to use the disks in parallel all the time (RAID), as its noisy, needs a large housing for the computer and most important it is prone to problems (problems with motherboards or power supply, lightnings etc.)

Also instead of "just" a checksum (CRC32, MD5, ...), an error correcting code  would be nice. The only example I could find about that idea is RCFFS  (from "Adding Aggressive Error Correction to a High-Performance  Compressing Flash File System") - but as the title says, this is a  flash-system.

Of course, deduplication and compressing are a plus, but minor advantages imo.


Any ideas/thoughts/suggestions from your site about a good backup strategy for home users?!

Thank you ;)

---

### Post by TheFu on 2015-09-25
Use rsync for the mirroring. You can automate it with a tiny script, then run that script daily, weekly, monthly from cron.  Something simple like, 
```
/usr/bin/rsync -av --stats --progress --delete-before /misc/2TB/* /misc/b-2T/
```

rsync is NOT sufficient for system backups. It really is only good enough for huge media files that never change, not files that change.

If the system doesn't have ECC RAM, forget ZFS. There are important reasons for this.

BTRFS is very new. Some people are willing to trust it. To me, nothing is more important than data and I'm unwilling to trust a FS that isn't completely trusted throughout the Linux community.  New doesn't mean better. It often means "untested or not-ready-for-general-use."

Hopefully, you'll get some other, less biased, opinions too. ;)

For backups, I like rdiff-backup. It isn't perfect, but meets our small company needs.  Daily, backups, automatic, for about 20 systems with 30-120 days of backup sets for each. If 30 days of system backups takes only 1.10x the original storage, why not?  Versioned backups are absolutely critical. Best introduction: [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)

On paper, I would much prefer duplicity for backups, but in my testing, never got it to work acceptably. Plus it is "old-school" style - weekly full system backups with daily incrementals.

If you want checksums for files, instead of using a file system, perhaps an add-on like par2 which creates parity files would be better? Knowing there is an issue is 1 thing, with par2 files (10%), and small errors can be corrected.  [http://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](http://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2) explains a method with commands to recover corrupted data.  Short of ZFS, I wouldn't trust any file system without par2 files to validate important data over long periods.

---

### Post by buntunoob2 on 2015-09-25
Thank you for your answer. Do you have a source for an explanation why ECC is mandatory for ZFS? I'm curious about that reason.

I know par2, but only for static data. Afaik it builds recovery information on a per-directory basis. - so It has to be rebuild when new files are added to a directory, right?!
besides the fact that it is inconvenient to have files for these meta information (of course you can use hidden files)

rsync is basically what I do today - besides the fact, that I check manually in order to detect silent data corruption on the source side. Even with rdiff of x days I would have a problem with silent data corruption, if I do not notice it within an x day period.

---

