---
title: "Folders now appears as files"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by danielrs on 2008-05-26
I have an external hard-drive with backups and stuff like that. Today, I plugged it on my computer (with Gutsy) and some (not all) folders appears as as files...

These files don't have any extension and I don't know what happened.

Please help me.

---

### Post by chrisccoulson on 2008-05-26
Is it formatted as FAT32? What is the output of:
```
grep -i panic /var/log/syslog
```
...after you've plugged it in?

---

### Post by danielrs on 2008-05-26
I think it is formated FAT32, but I'm not sure, but I know I formated it on Windows XP.

When I run that command in the console, it doesn't display any output...

---

### Post by danielrs on 2008-05-26
Ubuntu says it's formated as: "vfat", I assume it shoild be FAT32...

---

### Post by damis648 on 2008-05-26
Hm that is interesting... If i were you i dont know, maybe temporarily save the data somewhere else and try formatting the drive as NTFS or Ext3. And that might work out better.

---

### Post by danielrs on 2008-05-26
I forgot to say: that already happened to me o a flash drive. (An old one, with 128MB)

---

### Post by NormR2 on 2008-05-26
What do you see from list commmand: ls -l

---

