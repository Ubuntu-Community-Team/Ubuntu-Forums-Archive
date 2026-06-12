---
title: "tar --one-file-system"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by risk3715 on 2014-05-06
If I'm backing up my system, I like to use tar with the --one-file-system option. Does this exclude home directories? I know they exclude the /proc, /sys, /mnt, /media, /run and /dev directories. If I want to include the home directory, do I have to manually exclude all the others?

---

### Post by Impavidus on 2014-05-06
If you have a separate /home partition, it should exclude the /home directory. Else it should include it.

You can also make separate backups for /home and other things. Maybe you want more frequent backups of one than of the other.

---

