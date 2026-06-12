---
title: "look if the directory is empty in bash"
date: 2007-07-21
forum: Programming Talk
---

### Post by cazz on 2007-07-21
How can I make so the bash file can see if a directory is empty or not.

---

### Post by Mr. C. on 2007-07-21
```
if [ $(ls -1A | wc -l) -eq 0 ]; then
    echo Empty
fi
```

MrC

---

