---
title: "merging partitions went wrong..."
date: 2008-06-10
forum: New to Ubuntu
---

### Post by vincentvega_1985 on 2008-06-10
guys i need help!

i have a 500gig external hd, which is seperated into a 100gig and a 400 gig partition. I have data on both of them, and wanted to merge the two partitions. i used partition magic in windows (i also have ubuntu by the way), but the damn program crashed half way through the job.

after restarting my machine, the 100gig partition is unharmed, but the 400gig one appears as unformated. is there any way to fix this? i really don't want to lose the data!

i'd appreciate someones help!

cheers, vincent

---

### Post by gr4nf on 2008-06-10
Which one is the linux partition?

---

### Post by vincentvega_1985 on 2008-06-10
> **gr4nf said:**
> Which one is the linux partition?

no, i think you misunderstood.
this is an external harddrive , i only have data on it. both ntfs partitions.

---

### Post by Duck2006 on 2008-06-10
These may help.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntuforums.org/showthread.php?t=417761](http://ubuntuforums.org/showthread.php?t=417761)

---

### Post by cariboo on 2008-06-10
Since this question really has nothing to do with ubuntu I would say their are plenty of threads on this forum about recovering data from partitoning mistakes. If you would like to use ubuntu to recover your data you're going to have to give us a little more information.

First in a terminal:

```
fdisk -l
```


Paste the info in a post and we can go from there.

Jim

---

