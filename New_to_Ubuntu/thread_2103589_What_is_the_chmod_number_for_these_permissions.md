---
title: "What is the chmod number for these permissions?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2013-01-10
what numbers results in these permissions (folders not files) ```
chmod ### /path/to/dir
```as listed by ls -l
```
drwxr-xr-x
drwx------
```

---

### Post by cmoraes on 2013-01-10
For 
drwx------     chmod 700
drwxr-xr-x    chmod 755
 
see [http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html) for more examples.

---

### Post by steeldriver on 2013-01-10
FYI you can always use 'stat' to look at the octal mode directly

```
$ stat -c '%a' *dir*
```FYI(2) you can specify the file mode symbolically in chmod

```
chmod u=rwx,g=,o= *dir*
```

---

### Post by tlhIngan on 2013-01-10
> **pqwoerituytrueiwoq said:**
> what numbers results in these permissions (folders not files)

Numbers are just a shorthand way of assigning permissions.
You can always use the long way:
u for owner
g for group
o for others
a for all
+ to add
- to remove
x for execute
r for read
w for write

```
tlhingan@Amanda:~$ ls -l out.pnm
--w------- 1 root root 410235 Jan  5 13:05 out.pnm
tlhingan@Amanda:~$ sudo chmod o+w out.pnm
tlhingan@Amanda:~$ ls -l out.pnm
--w-----w- 1 root root 410235 Jan  5 13:05 out.pnm
tlhingan@Amanda:~$
```

---

### Post by Elfy on 2013-01-10
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

I found that page, with the boxes to fiddle in, useful

---

