---
title: "chmod question"
date: 2005-09-11
forum: Programming Talk
---

### Post by z-vet on 2005-09-11
Hi all.
I need to change permission for directory and it´s subdirs. Running ´chmod -R a+x some_dir´ changing permissions for all of this directory´s content, including files. How can i change permissions for directory and subdirectories but leave a permissions for files unchanged?

---

### Post by LordHunter317 on 2005-09-11
You could use find:```
find ./ -type d -print0 | xargs -0 chmod perms
```Or, if you don't want to grant execute on files (unless they already have it) use a+X.

---

