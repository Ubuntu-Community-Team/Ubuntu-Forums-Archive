---
title: "GTK spinboxes dialogs and checkboxes"
date: 2010-01-01
forum: Programming Talk
---

### Post by J V on 2010-01-01
I have problesm with these three widgets.

Dialog: For some reason whenever my dialog pops up (not about, just a generic dialog) the thick text at the top is highlighted...

[[IMG]http://img705.imageshack.us/img705/981/screenshotapghelp.th.png[/IMG]]("http://img705.imageshack.us/i/screenshotapghelp.png/")

I used a cheap set_value() hack to fix the spinboxes

Checkboxes
```
        def check_toggled(self,widget):
        if(widget.get_inconsistent()):
            widget.set_active(True)
            widget.set_inconsistent(False)
        elif(widget.get_active()):
            widget.set_inconsistent(True)
        return True
```Edit: fixed

---

### Post by J V on 2010-01-02
Bump, still need a word on why the dialog title is highlighted :/

---

