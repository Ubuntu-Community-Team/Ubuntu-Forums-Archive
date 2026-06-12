---
title: "Bug in (py)gtk or me doing something stupid?"
date: 2008-02-11
forum: Programming Talk
---

### Post by Jimmy_r on 2008-02-11
I have made a minimal example to demonstrate this problem.


```
#!/usr/bin/env python

import gtk

main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
main_window.set_icon_from_file("test.svg")
dialog = gtk.Dialog(**parent=None**)
dialog.show()
dialog.hide()
main_window.show()
gtk.main()
```

Works without problems.

But this:
```
#!/usr/bin/env python

import gtk

main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
main_window.set_icon_from_file("test.svg")
dialog = gtk.Dialog(**parent=main_window**)
dialog.show()
dialog.hide()
main_window.show()
gtk.main()
```

will output the message:
> test.py:13: GtkWarning: gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed
  self.main_window.show()

And will not display the icon.

So is this a gtk bug, or am I trying to do something that I am not supposed to do?

---

### Post by Jimmy_r on 2008-02-12
Also, setting the parent of dialog to main_window does not do any harm, as long as the dialog is not shown before the main window is.

This will show the icon:

```
#!/usr/bin/env python

import gtk

main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
main_window.set_icon_from_file("test.svg")
dialog = gtk.Dialog(parent=main_window)
[B]main_window.show()
dialog.show()[/B]
gtk.main()
```

This will not:

```
#!/usr/bin/env python

import gtk

main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
main_window.set_icon_from_file("test.svg")
dialog = gtk.Dialog(parent=main_window)
[B]dialog.show()
main_window.show()[/B]
gtk.main()
```

I am really curious to what causes the > gtk_window_realize_icon: assertion `info->icon_pixmap == NULL' failed when a child dialog is shown before the main window.

---

### Post by Quikee on 2008-02-12
If I am not mistaken main window has to be realized (show() triggers realize) before you realize the child (dialog) window. This is probably the cause of the warning. Usually you don't call show() for every widget but call show_all() on the main window once you are done building widgets. Like:

[PHP]main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
main_window.set_icon_name("folder")
dialog = gtk.Dialog(parent=main_window)
main_window.show_all()
gtk.main()[/PHP]

If you do show and hide in the same time is the same as if you did not do nothing as gtk.main() has not yet been called.

---

### Post by Jimmy_r on 2008-02-12
Thank you for the information.

The
```
dialog.hide()
```
in my first post was basically a remnant of the code in my real app, where I encountered the problem. I removed that for the other post since it was not needed to reproduce the problem.

This is how the app works:
First a dialog with a progressbar is shown while some pre-initialization is done in a separate thread. When that is done, the dialog is destroyed and the main window shown. Why the main window is not shown behind the progress dialog is because the widgets on the main window are shown or remain hidden based on the data from the pre-init work. Therefore I have the main window hidden until everything is done to make things a bit less ugly.

Anyway, thanks for the info on realizing the main window. I will look into it when I get home.
Funny thing is that I cannot remember why I had to make the dialog a child of the main window in the first place :)

For the record, here is the code where I encountered the problem: [http://startup-manager.svn.sourceforge.net/viewvc/startup-manager/trunk/data/gtk_frontend.py?revision=27&view=markup](http://startup-manager.svn.sourceforge.net/viewvc/startup-manager/trunk/data/gtk_frontend.py?revision=27&view=markup)

---

### Post by Jimmy_r on 2008-02-12
Thanks for getting me on the right track. This works:
```
#!/usr/bin/env python

import gtk

main_window = gtk.Window(gtk.WINDOW_TOPLEVEL)
main_window.set_icon_from_file("test.svg")
**main_window.realize()**
dialog = gtk.Dialog(parent=main_window)
dialog.show()
main_window.show()
gtk.main()
```

---

