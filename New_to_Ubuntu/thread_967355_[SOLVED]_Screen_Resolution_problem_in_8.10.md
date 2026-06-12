---
title: "[SOLVED] Screen Resolution problem in 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by sooperspook on 2008-11-02
I don't know what happened. One day it's fine now the screen resolution is something huge (1450 x 1050 or something like that)

In fact a third of my desktop is not visible on my screen!

Worse yet, the Screen Resolution option in Preferences is not there any more so I can't even change it!

Has this happened to anyone else? How do I fix it?

---

### Post by scragar on 2008-11-02
I do believe that the option your thinking of is part of the gnome control centre. Try reinstalling it, but first try running it from a terminal.

```
gnome-display-properties
## and if that doesn't work reinstall the ap:
sudo apt-get install --reinstall gnome-control-center
```

---

### Post by sooperspook on 2008-11-02
Sweet! That worked.

Thanks mate! :D

---

