---
title: "Backup Error"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-13
Hey guys, so I finally have 12.04 setup the way I like it so I'd like to make a backup of it...I am trying to use Deja Dup which came preinstalled, to backup my home folder to a NTFS drive that is mounted at boot I have read/write access to but I get the error below:

[IMG]http://i.imgur.com/gMPPhl.png[/IMG]

Note that the directory does exist, and this was previously working under 11.10 (deja dup + same harddrive and directory) :confused:

---

### Post by Old_Grey_Wolf on 2012-05-13
Try removing the / at the beginning of the backup location.

---

### Post by d4m1r on 2012-05-13
> **Old_Gray_Wolf said:**
> Try removing the / at the beginning of the backup location.

Wow, thanks! That's all it took. That message is decieving as it made it seem like a permissions issue....

---

