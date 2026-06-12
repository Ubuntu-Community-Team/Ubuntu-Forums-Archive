---
title: "[SOLVED] Terminal while running python"
date: 2007-05-21
forum: Programming Talk
---

### Post by holihue on 2007-05-21
What command do I need if I want to start a terminal when I run a .py file.

And to have the terminal closed after the script is stopped.



Thanks

---

### Post by Jussi Kukkonen on 2007-05-21
That depends on the terminal software you use. See the manual page of your terminal program. With gnome-terminal, you'd do something like  this:
```
gnome-terminal -x python your-python-file.py
```

EDIT: now that I read your question again, I'm not sure if you actually want to start the terminal from python instead... Be a bit more verbose if you want more help.

---

### Post by holihue on 2007-05-21
gnome-terminal -x python



Thanks

---

