---
title: "command help my mind is going"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by klein de usa on 2008-11-13
hi 
it has been a while, and i can't remember how to set gedit as the default editor in terminal i have done it before but don't know how i did it.

---

### Post by snova on 2008-11-13
Perhaps you were looking for this:

```
export EDITOR=gedit
```

Added to your .bashrc file (or equivalent startup file for alternative shells), this will set the editor for all programs that respect this variable.

---

### Post by klein de usa on 2008-11-13
yes 
thank you, i was drawing a blank,

---

