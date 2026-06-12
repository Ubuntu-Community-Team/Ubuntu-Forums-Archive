---
title: "Determining when a GNOME session ends"
date: 2008-04-10
forum: Programming Talk
---

### Post by kevykev on 2008-04-10
Hi All,

Just wondering if anyone knows a good way to determine when a GNOME session ends programmatically? I want to use a gobject mainloop (which listens for DBUS messages) and terminate the loop when the session ends. 

At the moment, I'm working around it using a gtk.main() loop instead of the gobject loop. However, because there is no UI elements in the program, I'd rather not have gtk as a dependency. Also, the shutdown isn't clean with the gtk.main() solution - the program terminates with an error message saying that the connection to the display was lost.

Any ideas? The program is in python btw.

Thanks,
-Kevin

---

