---
title: "Which file type to use when formating"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by Tazmman on 2013-12-01
I've decided to a new thread from the original ["search system files for salvage]("http://ubuntuforums.org/showthread.php?t=2191101") ". Seeing how it was to obtain a hard drive, strictly for storage purposes. 
I'm formatting a different Hard now. And I'm wondering which file type might be better for my purpose. 
I'm using strictly Linux at the time. so would one of the Reiser types( I'm assuming  that what ext 2 & 4 are),  or this encrypted FAT type for Linex, be better For file  transfer speeds?
And would, not using The all comp. FAT restrict me for "Slaving" on a Windows OS?

---

### Post by philinux on 2013-12-01
Ext4 is what I've been using for ages. On a Linux only system

---

### Post by Tazmman on 2013-12-01
Ok. Here's farther question. Would formatting it while as a "Sudo user" help open up the permission if I were slave it to a different Ubuntu machine?

---

### Post by bab1 on 2013-12-01
> **Tazmman said:**
> Ok. Here's farther question. Would formatting it while as a "Sudo user" help open up the permission if I were slave it to a different Ubuntu machine?
The permissions are not affected by having root ("Sudo user") format the disk partitions.  You don't "slave" additional disks at all.  You mount the file system on the new partition to the existing file system.

---

### Post by BenjaminCHILOE IS. on 2013-12-01
yes I've also been using ext 4 for erasing and reinstalling  as clean on.... About your second question, how many hard disks are u using in your actual machine ?

---

### Post by Tazmman on 2013-12-01
> **bab1 said:**
>   You don't "slave" additional disks at all.  You mount the file system on the new partition to the existing file system.

Yes. Thank you For correcting me.:wink: It's always best to use the correct terminology  .

---

### Post by bab1 on 2013-12-01
> **Tazmman said:**
> Yes. Thank you For correcting me.:wink: It's always best to use the correct terminology  .

Ya, just never know what the other person is thinkin'.  :-)

---

### Post by jimmyh1972 on 2013-12-03
EXT4 definitely!

---

### Post by oldfred on 2013-12-03
Some have tested various formats.

 10-Way Linux File-System Comparison On Linux13.10
[http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_310_10fs&num=1)
BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
Linux 3.11 File-System Performance: EXT4, Btrfs, XFS, F2FS
[http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_311_filesystems&num=1)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)
[http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE](http://www.phoronix.com/scan.php?page=news_item&px=MTM1MTE)

If you do have to use with Windows then you have to use NTFS, but you need Windows or a Windows repairCD/flash drive to run chkdsk periodically.

---

