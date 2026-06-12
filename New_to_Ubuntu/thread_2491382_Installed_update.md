---
title: "Installed update"
date: 2023-10-06
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-10-06
Does, when you install update. the old file will get deleted?

so i dont need to worry, after each update, my storage doesnt fill up.

---

### Post by ian-weisser on 2023-10-06
> **rifqilubis said:**
> Does, when you install update. the old file will get deleted?

Generally yes.

In some cases one or two older versions are retained. Not dozens.

---

### Post by rifqilubis on 2023-10-06
is it alright to delete folder that retained?

like what is the purpose?

---

### Post by ian-weisser on 2023-10-06
No, it's often not alright. Depends upon the directory ("folder") that you envision eviscerating.

The purpose is usually to provide a fallback in case of a broken upgrade. So your system and key applications still work.

Removing packages is among the most laborious and least efficient ways to reclaim storage space. Lots of work to reclaim very little space. You could spend a whole day reclaiming less than the space occupied by a single movie.

---

### Post by rifqilubis on 2023-10-06
oh nice info, thanks. i will solve this thread.

---

### Post by Rubi1200 on 2023-10-07
If you want to see what is taking up space on the install, use this command in the terminal:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

---

### Post by rifqilubis on 2023-10-07
nice, thanks.

---

