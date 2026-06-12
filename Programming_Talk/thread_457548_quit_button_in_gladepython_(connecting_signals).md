---
title: "quit button in glade/python (connecting signals)"
date: 2007-05-28
forum: Programming Talk
---

### Post by braddcadd on 2007-05-28
The main window destroys correctly in my class but the quit button does not.  Any ideas?

Except from my __init__ function:
```

dic = { 
        "on_add_clicked" : self.addfile,
        "on_remove_clicked" : self.removefile,
        "on_up_clicked" : self.moveup,
        "on_down_clicked" : self.movedown,
        "on_join_clicked" : self.join,
        "on_quit_clicked" : gtk.main_quit,
        "on_main_destroy" : gtk.main_quit 
        }
        self.wTree.signal_autoconnect(dic)

```

Thanks for any help.

---

### Post by braddcadd on 2007-05-29
Well, at least I'm not going crazy (yet).  This code actually works when called from the terminal.  For some reason it just doesn't work in ERIC (run or debug mode).

---

