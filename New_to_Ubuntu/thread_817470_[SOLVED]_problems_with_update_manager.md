---
title: "[SOLVED] problems with update manager"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by default00 on 2008-06-03
when i try to use the update manager i get an error saying i cant download all repository indexes. The first line of the error messages says "Failed to fetch cdrom:[Ubuntu 8.04_Hardy Heron_-Release i386 (20080423))]/dists/hardy/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs" The second line says the same thing except its "/dists/hardy/restricted/binary-i386/Packages.gz" The third line just says "Some index files failed to download, they have been ignored,or old ones used instead" What can i do to fix this problem?

---

### Post by useResa on 2008-06-03
Most of the time the error occurs when the repository is (temporary) off line.
Nine out of ten times the error disappears when you try it again in a few minutes.

---

### Post by spiderbatdad on 2008-06-03
System>>Administration>>Software Sources. Uncheck cdrom.
The other issue looks like an error in your sources.list file: /etc/apt/sources.list Comment out the offending line.

Or post the file here for more help.

---

### Post by default00 on 2008-06-04
yeah unchecking cdrom in the software sources seemed to do the job. Thanks

---

