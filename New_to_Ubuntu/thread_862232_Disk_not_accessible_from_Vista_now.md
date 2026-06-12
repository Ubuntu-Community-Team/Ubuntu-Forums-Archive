---
title: "Disk not accessible from Vista now"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Cront on 2008-07-17
Hi guys,

I have a couple of hard drives in my computer and since using ubuntu one of them is no longer accessible in vista.  I get an error along the lines of "H:\ is not accessible The directory or file is corrupted and unreadable"

The thing is I can access it fine in Ubuntu.  I've tried unmounting the drive before rebooting but to no avail.

Any ideas?

I'm using 64bit Ubuntu on the 2.6.24-19 kernel and 32bit Vista SP1

Thanks,

Cront

---

### Post by mikewhatever on 2008-07-17
I don't think Vista can read ext3 file system. Apparently, nothing is wrong with that partition.

---

### Post by Morpheun on 2008-07-17
Did you format the disk for ubuntu? If so Windows generally has a difficult time reading the default linux filesystem (ext3)

---

### Post by Morpheun on 2008-07-17
> **mikewhatever said:**
> I don't think Vista can read ext3 file system. Apparently, nothing is wrong with that partition.

Oh and if you REALLY do need to view those files with vista install [this]("http://www.fs-driver.org/"). Thats what I use on my rarely used Vista boot partition, I recomment turning on read only because it's still gonna have plenty of issues writing to ext2/3

---

### Post by Cront on 2008-07-17
Sorry I should have mentioned the file system is NTFS
Also Chkdsk finds no errors and Testdisk has not helped

---

