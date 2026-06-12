---
title: "difference between two directories"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Sarah L on 2008-11-18
Hi,
I've been manually backing up a folder on my computer to an external hard drive. Now that my internal HDD is running out of space, I'd like to delete the copy of the files on my computer. However, before I do this, I want to make sure that everything is backed up on my external hard drive. Is there a way to compare the contents of two directories and display the differences?

Thank you! :)

---

### Post by snova on 2008-11-18
```
diff --brief --recursive <dir 1> <dir 2>
```

PS. You may also wish to look into rsync as a backup tool, rather than just copying files.

---

