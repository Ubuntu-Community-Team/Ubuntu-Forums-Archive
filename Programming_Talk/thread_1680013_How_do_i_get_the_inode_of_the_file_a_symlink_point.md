---
title: "How do i get the inode of the file a symlink points to (bash)?"
date: 2011-02-01
forum: Programming Talk
---

### Post by ridetheteapot on 2011-02-01
I am using ```
ls -i `ls -l $slink | awk '{print $10}'`
``` or ls -i readlink 
but is there a more direct way?

---

### Post by sisco311 on 2011-02-01
You could use the stat command. Something like:
```
stat -L --format '%i' link
```

---

### Post by Arndt on 2011-02-02
> **ridetheteapot said:**
> I am using ```
ls -i `ls -l $slink | awk '{print $10}'`
``` or ls -i readlink 
but is there a more direct way?

```
ls -Li $slink

```

---

### Post by ridetheteapot on 2011-02-02
thanks both of you

> ls -Li $slink
lol i guess i should rtfm.
pretty simple, double thanks.

---

