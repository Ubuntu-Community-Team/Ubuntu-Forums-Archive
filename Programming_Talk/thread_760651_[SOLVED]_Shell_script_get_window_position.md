---
title: "[SOLVED] Shell script: get window position"
date: 2008-04-20
forum: Programming Talk
---

### Post by x1a4 on 2008-04-20
Hi,

How do I get the position of a window using its id which is stored in $wid? 

Thank you.

EDIT: Figured it out
```

x=$(xwininfo -id $wid | grep "Absolute upper-left X")
x=${x:25}
y=$(xwininfo -id $wid | grep "Absolute upper-left Y")
y=${y:25}

```

---

