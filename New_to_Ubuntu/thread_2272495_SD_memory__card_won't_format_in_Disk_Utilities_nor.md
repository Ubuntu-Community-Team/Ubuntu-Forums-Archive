---
title: "SD memory  card won't format in Disk Utilities nor in GParted or any other utility"
date: 2015-04-07
forum: New to Ubuntu
---

### Post by yashas73 on 2015-04-07
In Disk Utilities when i try to format my 8 Giga external Memory Card or even 32 Gig, I get this error :

Error creating partition

Error creating partition on /dev/sdb: Command-line `parted --align optimal --script "/dev/sdb" "mkpart primary ext2 1MiB 8053063679b"' exited with non-zero exit status 1: Error: You requested a partition from 1049kB to 8053MB (sectors 2048..15728639).
The closest location we can manage is 1049kB to 2212kB (sectors 2048..4321).
 (udisks-error-quark, 0)




I have tried in Ubuntu and Opensuse many time to format them but same errors
any one can help please ?

---

### Post by kerry_s on 2015-04-07
first delete them, then create a new partition in the format you want.

in disks that's the - sign, then format
in gparted just select delete, then new

---

