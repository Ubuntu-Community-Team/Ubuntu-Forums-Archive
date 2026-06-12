---
title: "Bash script question"
date: 2011-07-25
forum: Programming Talk
---

### Post by i8163264128 on 2011-07-25
what I tried to do is make a script that prints the id of the longest running process with a particular label, what I came up with is :

[PHP]#!/bin/bash

ps  -elfo pid,etime  |  grep "$1$"  |  sort  -r  -k 2,2  |  head -n 1 |  awk '{print $1;}'[/PHP]

but (perhaps unsurprisingly) it does nothing... can anyone give me some advice here?

/noob

---

### Post by Vaphell on 2011-07-25
```
ps  -elfo pid,etime
ERROR: Conflicting format options.
```

your first step fails, try ```
ps efo pid,etime
```

---

### Post by Habitual on 2011-07-25
It's always going to be 'init' (1).

---

