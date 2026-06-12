---
title: "Driver programming in Ubuntu"
date: 2010-06-02
forum: Programming Talk
---

### Post by devesa on 2010-06-02
Dear all,

I would like to write a HDD driver in Ubuntu, so that I could process some actions. For example, when I try to drag a file in my desktop and drop on this HDD, this operation was transformed in a encryption file on HDD.

Anyway, my question is. Is there an easy way to write drivers in Ubuntu (as easy as minifilters technique in Windows).

Thank you very much!

---

### Post by diesch on 2010-06-02
For thinks like that you don't need a disk driver but a file system. The easiest way to write your own file system is using [FUSE](http://fuse.sourceforge.net/).

---

### Post by devesa on 2010-06-02
Thank you! Is there any other one for kernel space instead of user space (FUSE)?

---

### Post by diesch on 2010-06-02
Have a look at [FiST](http://www.filesystems.org/)

---

### Post by devesa on 2010-06-02
That's perfect. Thank you!

---

