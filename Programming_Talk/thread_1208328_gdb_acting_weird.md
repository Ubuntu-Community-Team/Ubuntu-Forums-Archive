---
title: "gdb acting weird"
date: 2009-07-09
forum: Programming Talk
---

### Post by Sockerdrickan on 2009-07-09
p is supposed to print the value of a variable right?

```
const unsigned int rolf=500;
(gdb) p rolf
$1 = 4198984
```
:mad:

---

### Post by TheStatsMan on 2009-07-09
Have you turned compiler optimisations off?

---

### Post by dwhitney67 on 2009-07-09
> **Tux0r said:**
> p is supposed to print the value of a variable right?

```
const unsigned int rolf=500;
(gdb) p rolf
$1 = 4198984
```
:mad:

From your output above, it would seem to me that the statement has not been executed yet.  Perform a "next" or a "step", then print the value of rolf.

---

