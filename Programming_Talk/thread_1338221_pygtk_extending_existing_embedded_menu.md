---
title: "pygtk extending existing embedded menu"
date: 2009-11-26
forum: Programming Talk
---

### Post by giuspen on 2009-11-26
hi,
I'm working upon a gtk.TextView that has its own right-click menu,
but I would like to add some menu items to it, does anybody know how to do it?
I'm able to create a totally new menu and associate it to the right click event but doing this i have then 2 menus.
thanks in advance.

---

### Post by diesch on 2009-11-26
Connect a callback to the textview's* populate-popup* signal. The callback gets the menu as the second parameter[I].
[/I]

---

### Post by giuspen on 2009-11-27
> **diesch said:**
> Connect a callback to the textview's* populate-popup* signal. The callback gets the menu as the second parameter[I].
[/I]

thanks a lot

---

