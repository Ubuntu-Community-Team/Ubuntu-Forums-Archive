---
title: "Switch keyboard keys?"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by magisterludi1789 on 2012-03-19
So, I've accidentally poured nail polish remover over my keyboard and my Delete key has stopped working (the inner plastic holds are corroded).

It seems like a good idea to switch Delete and Insert, since I never use the latter, but I can't find how to do it. I've tried messing with xmodmap files but it doesn't work (maybe I'm doing it wrong!).

Any ideas?

btw, I'm running Ubuntu 11.10 (Gnome Classic)

---

### Post by PapaGary on 2012-03-19
Laptop or desktop?

---

### Post by TeoBigusGeekus on 2012-03-19
How did you try to do with xmodmap?

---

### Post by magisterludi1789 on 2012-03-19
PapaGary: Desktop.

TeoBigusGeekus: I did what I found on another forum, where someone recommended editing the file and replacing whatever's after the equals sign for the Insert and Del keys. Didn't work. Plus, it created another .Xmodmap file --> Xmodmap~ with the original content (autobackup?)

---

### Post by TeoBigusGeekus on 2012-03-19
Can you post your .Xmodmapfile?

---

### Post by idoitprone on 2012-03-19
```
xmodmap -e "keycode 118 = Delete"
``` to run in one line in the shell


save tis into file .Xmodmap
```
keycode 118 = Delete
```to run
```
xmodmap .Xmodmap
```I usually put tat code above in a scipt
```

#!/bin/bash

xmodmap .Xmodmap
```

if that does not work
```
sudo apt-get install x11-utils
```

run
```
xev
```
press insert and replace that number above right by keycode with the insert keycode

---

### Post by magisterludi1789 on 2012-03-19
thanks idoitprone!
first method worked just as fine.

---

