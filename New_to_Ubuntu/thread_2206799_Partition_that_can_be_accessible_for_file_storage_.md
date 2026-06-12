---
title: "Partition that can be accessible for file storage by ubuntu and windows 7"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by decka on 2014-02-20
hi guys, i have a problem here.
i have installed windows 7 and lubuntu 13.10 on my netbook everything is cool by far, here is the partition that i have created :
1. System Reserved for windows = 100MB
2. ntfs Local disk C: windows 7 file system = 70GB
3. ext4 lubuntu file system = 60GB
4. swap for lubuntu = 2GB
5. unallocated space = 180GB

now, i realize that windows can't read partition from ubuntu but on the other hand, ubuntu can do that.
so, i want to use all unallocated space i have for my media storage that can be accessible and used both by windows 7 and lubuntu.
what must i do? what partition should i make?

---

### Post by erind on 2014-02-20
> **decka said:**
> [...]

now, i realize that windows can't read partition from ubuntu but on the other hand, ubuntu can do that.
so, i want to use all unallocated space i have for my media storage that can be accessible and used both by windows 7 and lubuntu.
what must i do? what partition should i make?

The usual recommendation is a *NTFS* partition - ubuntu reads and writes just fine *NTFS*.

---

### Post by oldfred on 2014-02-23
If you have used all 4 primary partitions, you will have to convert one primary to a logical. 
But often default install puts swap in an extended partition. If so then you can extend the extended partition to include all of the unallocated and create another logical NTFS data partition. Both Linux & Windows will read a NTFS logical data partition.

If swap is not at end of drive next to unallocated it becomes a bit more complex.
Then post this:
sudo parted -l

---

### Post by decka on 2014-02-24
thanks guys, it worked... :)

---

