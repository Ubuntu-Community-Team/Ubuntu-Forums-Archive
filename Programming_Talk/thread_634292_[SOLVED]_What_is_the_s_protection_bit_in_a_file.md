---
title: "[SOLVED] What is the s protection bit in a file?"
date: 2007-12-07
forum: Programming Talk
---

### Post by Griff on 2007-12-07
For example when you run:
```
ls -l /usr/bin/passwd
```
to view the protection bits of passwd there is an s in the owner permission area.  What is that?  I thought there was only r, w, or x?
Here it is:
```
-rwsr-xr-x 1 root root 29104 2006-12-19 15:35 /usr/bin/passwd
```

---

### Post by aks44 on 2007-12-07
When in the first rwx group (the one which corresponds to the owner user), **S** is the [setuid]("http://en.wikipedia.org/wiki/Setuid") bit. In the second rwx group (owner group) it is the setgid bit.

When the file has both **x** and **S**, **s** is displayed. If the file doesn't have **x**, **S** is displayed.

---

### Post by Griff on 2007-12-08
Ah! Thank you!  I googled and searched but couldn't find anything relating to this. :)

---

