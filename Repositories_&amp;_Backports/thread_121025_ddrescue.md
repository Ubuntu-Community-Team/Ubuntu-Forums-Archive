---
title: "ddrescue"
date: 2006-01-24
forum: Repositories &amp; Backports
---

### Post by Berik on 2006-01-24
I've just installed ddrescue, to attempt to rescue data from a hard disk with a lot of bad blocks.
But when I attempt to run ddrescue, it tells me:
```
sudo: ddrescue: command not found
```

Does anyone know how to run ddrescue?

I am using kubuntu 5.10

---

### Post by tosszyx on 2008-12-15
A useful tool for looking for file locations is: whereis

In this case:

```
$ whereis ddrescue
ddrescue:
$ whereis dd_rescue
dd_rescue: /bin/dd_rescue /usr/share/man/man1/dd_rescue.1.gz
```

So we know that we should called like **dd_rescue**. From there you are just a **man dd_rescue** away !.

---

### Post by gotnix on 2008-12-16
ddrescue is in gddrescue

clone dying drive to new drive
```

ddrescue -v -r 1 /dev/sdx /dev/sdx Recovery.log

```

clone dying drive to image
```

ddrescue -v -r 1 /dev/sdx disk-image.img Recovery.log

```

use -r 1 to minimize retries to 1 so that it won't kill your disk retrying the same sector over and over

always use a log file. if the process gets interrupted it will pick up where it left off when restarted.


one other thing, why dig up an old thread?

---

