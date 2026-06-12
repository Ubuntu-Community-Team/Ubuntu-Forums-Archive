---
title: "Gnome backup done file based"
date: 2007-06-05
forum: Programming Talk
---

### Post by Death_Sargent on 2007-06-05
I am trying to make a way to back up .gnome and .gconf
the current script works as such
```
#! /bin/bash
mkdir "/home/pete/gnomebackup/`date`" && cp -r "/home/pete/.gnome" "/home/pete/.gconf" "/home/pete/gnomebackup/`date`"

```

I want to make it delete folders it made that are a certain amount of time older than the current back up.

---

### Post by Death_Sargent on 2007-06-06
*****push*****

---

