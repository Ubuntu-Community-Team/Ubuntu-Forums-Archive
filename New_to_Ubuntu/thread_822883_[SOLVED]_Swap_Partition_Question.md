---
title: "[SOLVED] Swap Partition Question"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ghindo on 2008-06-08
By default, Ubuntu created a swap partition 5.77 GB large.  That seems a bit large to me, as I have read that a swap partition only needs to be about as large as the amount of RAM one has, and I have 2 GB of RAM on my machine.  Would it be safe for me to shrink my swap partition to 2 GB?

Screenshot attached.

---

### Post by rickycodie on 2008-06-08
it wouldn't affect you at all, other than shrinking your swap size.

---

### Post by sam_delta on 2008-06-08
yeah, its safe, as long as you dont go down of 2gigs, cuz you need at least the same amount of your ram to hibernate/suspend

sam

---

### Post by ghindo on 2008-06-09
Sweet.  Thanks, guys :)

---

### Post by cariboo on 2008-06-09
Actually swap does get used during regular operation enter this command in a terminal to see how much swap you are using:

```
jimk@intrepid:~$ free
             total       used       free     shared    buffers     cached
Mem:       2030860    2013924      16936          0      49264     641056
-/+ buffers/cache:    1323604     707256
Swap:      9566656        600    9566056
```

Jim

---

