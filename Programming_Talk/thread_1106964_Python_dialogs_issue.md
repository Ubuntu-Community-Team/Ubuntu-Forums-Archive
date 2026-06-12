---
title: "Python dialogs issue"
date: 2009-03-26
forum: Programming Talk
---

### Post by Blutack on 2009-03-26
I'm having a problem with a Python/GTK problem that google can't solve.
When I show an about dialog, using the following piece of code:

```

    def about(self, widget):
        self.about.run()
        self.about.destroy()

```

It works perfectly the first time, but the second time I try to select it, I get a tiny window with no contents and the following error:

flyby.py:228: GtkWarning: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed
  self.about.run()

Does anybody please have any ideas about this?
It also throws the same error for a different dialog.
Cheers!

---

### Post by imdano on 2009-03-26
It sounds like you either need to rebuild the object before calling run() on it again, or use hide() instead of destroy().  Calling destroy() really does destroy the widget, you need to recreate before you can use it again.

---

### Post by Blutack on 2009-03-27
That's sorted it, many thanks!

---

