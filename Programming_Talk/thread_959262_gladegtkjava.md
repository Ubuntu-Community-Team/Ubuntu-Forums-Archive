---
title: "glade/gtk/java"
date: 2008-10-26
forum: Programming Talk
---

### Post by blackphiber on 2008-10-26
i have libjava-gnome-java installed.

I would like to use glade to develop my interface, I would assume it is libglade-java however it states
"Please be aware that this package is part of java-gnome 2.x series
which is deprecated.

The java-gnome project provides Java bindings for the GNOME platform."

pretty sure java-gnome was replaced by libjava-gnome-java...

so, to get glade going, what package(s) do I need to install (running intrepid)?

thanks


EDIT:
[http://library.gnome.org/devel/gtk/2.14/gtk-migrating-GtkBuilder.html](http://library.gnome.org/devel/gtk/2.14/gtk-migrating-GtkBuilder.html)

looks like libglade is being depreciated in favor of GtkBuilder which I cannot seem to find in Synaptic...

I hope this is not a silly question

---

### Post by komuthan on 2008-11-13
You just need libjava-gnome-java installed 
Then you can use .glade files in your java-gnome projects
there is a good example here
[http://research.operationaldynamics.com/bzr/java-gnome/mainline/tests/prototype/Designer.java](http://research.operationaldynamics.com/bzr/java-gnome/mainline/tests/prototype/Designer.java)

---

