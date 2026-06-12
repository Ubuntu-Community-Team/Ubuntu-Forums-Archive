---
title: "Error using glade 3.6 and pygtk (gtk builder)"
date: 2009-03-19
forum: Programming Talk
---

### Post by BlackLukes on 2009-03-19
Hi, I'm testing the new glade 3.6 with gtk.builder (using pygtk). The treeview widget seems to have a tag related problem:

```
Traceback (most recent call last):
  File "Gui.py", line 36, in <module>
    Gui()
  File "Gui.py", line 31, in __init__
    self.builder.add_from_file('Gui.glade')
glib.GError: Unhandled tag: 'data'
```





I attached a simple script, try to execute and see what you get. Can you help me figuring out the problem? Since it's unstable, could this be a bug?

---

