---
title: "[SOLVED] Reformat / to jfs from ext3"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-15
I'm in a LiveCD session. My root (sda1) is formatted ext3. Under GParted, in a LiveCD session is it safe to reformat the / to jfs?

---

### Post by taurus on 2008-11-15
Then you will destroy all your data on / if you format it to another filesystem.

---

### Post by taurus on 2008-11-15
By the way, you might want to look into /var, /tmp, /var/backups to make sure there are no large files taking up all your space on /.

```
sudo du -h /tmp
sudo du -h /var
```

---

### Post by Mark_in_Hollywood on 2008-11-16
While I'm not knerd enuff to know whether I've 'snuffed' my hard disk, I again (this is the 8th or 9th time) will do a clean install.

---

### Post by Mardoct909 on 2008-11-16
Changing filesystems is always a complete destruction of data.

---

