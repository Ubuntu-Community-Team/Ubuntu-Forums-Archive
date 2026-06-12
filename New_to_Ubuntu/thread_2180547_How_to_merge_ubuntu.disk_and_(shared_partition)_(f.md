---
title: "How to merge ubuntu.disk and (shared partition)? (from wubi)"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by Nid_BickDiggers on 2013-10-13
Hello all, I have a wubi install that I made an extra partition for so I could share ~40gb of stuff with windows without having to use another drive.   Wellllll.... windows can't read the drive, and I want to use the space for my wubi install now.  How do I delete it and make my wubi take up the free space?  I think the actual partition is ubuntu.disk, but since it is not a traditional partition, i have no idea how to "merge" the two.  Please help! ty :)

---

### Post by Kevin McCready on 2013-10-13
There are lots of partitioning tools around.
parted  is  a  disk  partitioning  and  partition resizing program.  It
       allows you to create, destroy, resize, move and copy

---

### Post by oldfred on 2013-10-13
You cannot merge a file & a partition. You can convert your wubi to a full partitioned install and if you have room make that install large enough for all your data. Best to have really good backups first.

 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

