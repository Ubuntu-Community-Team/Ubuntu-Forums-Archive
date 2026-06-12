---
title: "Use clonezilla (from software center) to backup sd card"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2014-04-29
I have never used clonezilla before, but to my knowledge it is one of the best programs for making a backup
could someone tell me how to use it to backup my sd card (3 partitions) to a file

---

### Post by sudodus on 2014-04-30
Clonezilla makes a complete cloned image (either a direct clone or a compressed image). It is a good way for complete but in-frequent backups. Other tools are better for frequent incremental backup (for example every night).

I run clonezilla booted from a separate CD or USB drive. I use the stable version, i686-pae, and I use the beginner mode most of the time, but I have also made a script to backup certain partitions in one computer, where I have a big multimedia partition, that I backup with Unison (because it is a waste of time to make full backups and to compress it).

[http://clonezilla.org/](http://clonezilla.org/)
[http://clonezilla.org/downloads/download.php?branch=stable](http://clonezilla.org/downloads/download.php?branch=stable)

Use the default method to make a compressed image (which is using partclone). An image of a whole drive can be restored to a blank drive of at least the same size.

Get an extra drive [with at least the same size as the source drive], and ***test*** restoring your system to that extra drive.

---

