---
title: "Same files are two different sizes."
date: 2013-04-21
forum: New to Ubuntu
---

### Post by Absolute Terror on 2013-04-21
I'm sure there's a simple explanation.

I'm backing up my PC to an external device and the backup is never the same. Same amount of files and subfolders but a size difference of 100 bytes or so. Why is this?

---

### Post by Impavidus on 2013-04-21
File size or disk usage? If your backup drive has a different block size it may change internal fragmentation, changing the disk usage for the same files. That's because drives are not addressable on byte level, only on higher level. The same happens if you first concatenate your files (like packing them in a tar archive). This reduces internal fragmentation and disk usage.

And I'm not sure about this, but the size of the directories themselves might change on a different partition type.

---

### Post by Absolute Terror on 2013-04-21
Both ext4, talking about actual number of bytes used.

---

