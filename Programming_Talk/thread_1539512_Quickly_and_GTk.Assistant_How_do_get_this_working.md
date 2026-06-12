---
title: "Quickly and GTk.Assistant: How do get this working?"
date: 2010-07-26
forum: Programming Talk
---

### Post by zefanja on 2010-07-26
Hello,

I'm starting to develop a little app with quickly. It is no problem to add a dialog with quickly add dialog foobar, but how can I add a Assistant?

I've tried to create a new *ui file and the *py file and make my adjustments. The assistant appears, but I couldn't close it. It seems that there is a problem with the signals.

Does anybody has a hint for me how to add a assistant to working main window?

Regards,
zefanja

---

### Post by frmdstryr on 2011-10-01
You have to reconnect the signals on the assistant.  This worked for me:

```
    def finish_initializing(self, builder): # pylint: disable=E1002
        """Set up the main window"""
        super(NetworkDriveMapperWindow, self).finish_initializing(builder)
        # Code for other initialization actions should be added here.
        self.connect("cancel", self.on_destroy)
        self.connect("apply", self.on_apply_clicked)
        self.set_forward_page_func(self.on_page_changed, None)
```

Also make sure Window.py is inheriting gtk.Assistant instead of gtk.Window

---

