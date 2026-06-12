---
title: "Finding iNodes ?"
date: 2007-09-12
forum: Programming Talk
---

### Post by NuNn DaDdY on 2007-09-12
Is there any way to get to/look at the iNodes on the computer?

---

### Post by psusi on 2007-09-12
What do you mean?  An inode is a file.  Or more specifically, the block that describes the file's size, location, mode, and access timestamps.

---

### Post by slavik on 2007-09-12
stat and open :)

gotta love C :)

---

### Post by ghostdog74 on 2007-09-12
> **NuNn DaDdY said:**
> Is there any way to get to/look at the iNodes on the computer?

man ls. there's an option to look at inode of files.
Also check man page for GNU find command. hint: -inum, printf format.

---

### Post by slavik on 2007-09-13
well, good point, ls -l can list all the information written in an inode ...

but what exactly do you want to see in an inode? or do you want to estimate how much disk is used by them?

---

