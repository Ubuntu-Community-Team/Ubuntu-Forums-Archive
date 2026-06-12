---
title: "pygtk messagedialog and popups"
date: 2009-05-15
forum: Programming Talk
---

### Post by craftybones on 2009-05-15
Hello,

There seems to be a weird problem with gtk.Window(WINDOW_POPUP) and gtk.MessageDialog. I have the following:

----
moonwolf@trantor:~/python/gtk$ cat foo.py 
#! /usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk

window1 = gtk.Window()
window2 = gtk.Window(gtk.WINDOW_POPUP)
dummy_layout = gtk.Entry()
dummy_layout.text = "Window 2"
window2.add(dummy_layout)
window3 = gtk.MessageDialog(parent=window1,message_format="WINDOW 3!!!!")

window1.show()
#window2.show()
window3.show()

gtk.main()
-----

According to this code, window3, the message dialog window should be on top. However, no matter what I try, as long as there is an unhidden popup window(in this case window2), the gtk.MessageDialog window always is shown beneath the popup window.

I have tried setting the transient parents as well.

Can anybody advice? This doesn't seem likely to be a gtk bug as the gtkmm c++ implementation works as well.

Thank you,

craftybones

---

### Post by crdlb on 2009-05-18
Why are you using gtk.WINDOW_POPUP in the first place? That window type is used by GtkMenu, GtkTooltip, and very little else. It creates a window that is not managed by the window manager (which means, among other things, that the user cannot move or restack it)

---

### Post by craftybones on 2009-05-18
My application works on a touchscreen and has to provide a keypad that has to stay above almost everything except an error dialog. IF you know of a better way than to use a popup to achieve the same thing then sure, I'd love to know that.

Thank you,

J

---

### Post by crdlb on 2009-05-20
Just set the keypad window to be transient for the application main window: ```
keypad.set_transient_for(main_window)
```

If there are multiple windows in your app that the keypad needs to be above, then you can do what the gimp does and set the window's type hint to Utility: ```
keypad.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_UTILITY)
```

---

