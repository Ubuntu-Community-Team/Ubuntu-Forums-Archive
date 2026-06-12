---
title: "Getting the child of a scrolled window"
date: 2011-09-18
forum: Programming Talk
---

### Post by nickos on 2011-09-18
How can i do that?

---

### Post by dwhitney67 on 2011-09-18
Contact social services.


P.S.  You may want to take another stab at presenting the issue you are having.  Try including at a minimum the language you are programming in, the graphics toolkit that you are using, perhaps what you may have attempted already, and any little bit of information that may help someone.

---

### Post by nickos on 2011-09-18
> **dwhitney67 said:**
> Contact social services.


P.S.  You may want to take another stab at presenting the issue you are having.  Try including at a minimum the language you are programming in, the graphics toolkit that you are using, perhaps what you may have attempted already, and any little bit of information that may help someone.

whoops sorry.Forgot to mention that.....


its GTK in C

---

### Post by cgroza on 2011-09-18
Check the GTK documentation of GtkContainer (I don't know GTK, but I guess a Scrolled Window is a container.): [http://developer.gnome.org/gtk/2.24/GtkContainer.html](http://developer.gnome.org/gtk/2.24/GtkContainer.html)
This is the function you may be interested in: [http://developer.gnome.org/gtk/2.24/GtkContainer.html#gtk-container-get-children](http://developer.gnome.org/gtk/2.24/GtkContainer.html#gtk-container-get-children)

---

### Post by nickos on 2011-09-18
yes but i want to get a GtkWidget value not a GList which i get from gtk_container_get_children()

---

### Post by nickos on 2011-09-18
please somebody help! :(

---

