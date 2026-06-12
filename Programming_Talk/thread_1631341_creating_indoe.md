---
title: "creating indoe"
date: 2010-11-26
forum: Programming Talk
---

### Post by pswin on 2010-11-26
hi how can i create an inode in /dev with out using mknode command?

---

### Post by Arndt on 2010-11-26
> **pswin said:**
> hi how can i create an inode in /dev with out using mknode command?

'mknod', you mean? The program 'mknod' is probably just a thin interface to the system call 'mknod'. See "man 2 mknod".

---

