---
title: "Unmounted drive list via python ?"
date: 2012-07-02
forum: Programming Talk
---

### Post by prismctg on 2012-07-02
How to get a list of unmounted partition via Python ?

---

### Post by ofnuts on 2012-07-02
> **prismctg said:**
> How to get a list of unmounted partition via Python ?
I would compare the output of "df" (which ought to contain all mounted partitions) with the output of "ls /dev/disk/by-path" (which ought to list all available partitions, mounted or not). But that's fairly low-tech, there could be a better way.

---

### Post by prismctg on 2012-07-02
> **ofnuts said:**
> I would compare the output of "df" (which ought to contain all mounted partitions) with the output of "ls /dev/disk/by-path" (which ought to list all available partitions, mounted or not). But that's fairly low-tech, there could be a better way.

OWw..... that's a great idea  .....

---

