---
title: "[Python] Set title in Konsole (and other terminals)"
date: 2012-11-16
forum: Programming Talk
---

### Post by Erik1984 on 2012-11-16
I found a method to change the title of the terminal from Python. However it doesn't seem to work for me in Kubuntu 12.10 and Konsole as terminal. [https://bbs.archlinux.org/viewtopic.php?id=85567](https://bbs.archlinux.org/viewtopic.php?id=85567)

The code that supposed to work is:
```

import sys
sys.stdout.write("\x1b]2;test\x07")

```

To quickly try out yourself:
Type ```
python
``` to enter the python shell and enter the two lines I quoted above.

This does not change the title in Konsole however. Neither do those lines give any errors. Is their another way to set the terminal title from within Python? Or is the problem just with KDE's Konsole?

---

### Post by spjackson on 2012-11-16
That command works in LXTerminal, and also in gnome-terminal.

According to [this page]("http://stackoverflow.com/questions/5373253/how-can-one-put-the-output-of-a-command-into-a-konsole-title-bar") you need to enable it in Preferences for Konsole, but I don't have KDE available at the moment to verify this.

---

### Post by Erik1984 on 2012-11-16
Thanks again spjackson for the quick reply. I'll try that later on and report back here :P

---

### Post by Erik1984 on 2012-11-16
So it's a Konsole specific 'problem'. After changing the tab tile to "%w" I get my custom titles. I'll mark this as solved. Thanks :P

---

