---
title: "Pygtk object properties"
date: 2008-08-05
forum: Programming Talk
---

### Post by bubba_169 on 2008-08-05
This is starting to bug me now, I want to set the wrap-mode property in a gtk.CellRendererText but I dont know how. I can see the property I want to change in the documentation I just dont know how to get to it as theres no associated method for it?

Does anyone know how to access and change an objects properties that doesnt have an associated method (i.e. set_wrap_mode)?

I'm guessing its a really simple answer that should be staring me in the face but after an hour of searching the net I still cant find it?

---

### Post by kknd on 2008-08-05
All objetcs that derives from GObject have property setters/getters.

I don't know the exact method name for python, but I think its:

renderer.set_property("wrap-mode", myWrapMode)

---

### Post by bubba_169 on 2008-08-05
[http://www.pygtk.org/docs/pygobject/class-gobject.html#method-gobject--set-property]("http://www.pygtk.org/docs/pygobject/class-gobject.html#method-gobject--set-property")

Thank you, traced it all back to the base object and found it :D

---

