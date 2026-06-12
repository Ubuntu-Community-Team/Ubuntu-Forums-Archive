---
title: "[SOLVED] Simple home folder backup question"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by Matthewthegreat on 2008-10-23
With the command line, how would you copy all the files and sub-folders from my home directory to a directory in my external hard drive, but only copy files and sub-folders that did not exist or were newer than the versions in the destination directory in external hard drive?

  I have my home folder backed up but I want to update it without rewriting all the files because that take a lot of time!

Thanks!!!

---

### Post by jordilin on 2008-10-23
> **Matthewthegreat said:**
> With the command line, how would you copy all the files and sub-folders from my home directory to a directory in my external hard drive, but only copy files and sub-folders that did not exist or were newer than the versions in the destination directory in external hard drive?

  I have my home folder backed up but I want to update it without rewriting all the files because that take a lot of time!

Thanks!!!

```
cp -auv sourcefolder targetfolder
```
u option is for update only if newer or not exists
v verbose
a = dpR preserve mod, links (without following them) and recursion

---

### Post by jordilin on 2008-10-23
> **jordilin said:**
> ```
cp -auv sourcefolder targetfolder
```
u option is for update only if newer or not exists
v verbose
a = dpR preserve mod, links (without following them) and recursion

Note: First do some tests with some files before going for it

---

### Post by Matthewthegreat on 2008-10-23
> **jordilin said:**
> ```
cp -auv sourcefolder targetfolder
```
u option is for update only if newer or not exists
v verbose
a = dpR preserve mod, links (without following them) and recursion

Yep that worked! Thanks!!!

---

