---
title: "question about sed"
date: 2006-03-22
forum: Programming Talk
---

### Post by jackrobinson on 2006-03-22
How do I use sed to replace the following phrase:
> **Load    "dri"**
with
> **#Load       "dri"**
in the file 
**abc.conf**
Thanks in advance

---

### Post by LordHunter317 on 2006-03-22
```
sed -i.bak -e's/^Load "dri"/#Load "dri"/' abc.conf
``` should work fine.

---

### Post by jackrobinson on 2006-03-22
Thanks a lot! That works :)

---

