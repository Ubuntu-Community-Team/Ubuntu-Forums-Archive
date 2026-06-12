---
title: "how am i supposed to backup my home folder??"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by T2manner on 2008-10-26
i keep trying to make a .7z of my home folder and i keep getting errors like this file doesn't exist.
and i can't any good backup software

---

### Post by Xiong Chiamiov on 2008-10-26
The simplest way is to tar and gzip it:
```

tar -pczf home_backup.tar.gz ~

```
You would untar it with
```

tar xvf home_backup.tar.gz

```

---

