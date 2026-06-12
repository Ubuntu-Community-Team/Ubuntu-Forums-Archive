---
title: "Preference wont load with AWN"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by nilsolaris on 2008-05-21
I now have AWN (Avant Window Navigator) installed, but each time i go to the preferences window it opens for a second and then closes? Any suggestions?

---

### Post by aktiwers on 2008-05-21
> **nilsolaris said:**
> I now have AWN (Avant Window Navigator) installed, but each time i go to the preferences window it opens for a second and then closes? Any suggestions?

Is awn-manager installed?
```
sudo apt-get install awn-manager
```

if yes, does it give you any errors when you load it from terminal?
```
awn-manager
```

---

### Post by nilsolaris on 2008-05-21
It gives me this

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkComboBox::appears-as-list' of type `gboolean' from rc file value "((GString*) 0x868e560)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::row-ending-details' of type `gboolean' from rc file value "((GString*) 0x868e0a0)" of type `GString'
Segmentation fault

---

### Post by nilsolaris on 2008-05-21
Any others?:S

---

### Post by moonbeam on 2008-05-21
> **nilsolaris said:**
> It gives me this

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkComboBox::appears-as-list' of type `gboolean' from rc file value "((GString*) 0x868e560)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkTreeView::row-ending-details' of type `gboolean' from rc file value "((GString*) 0x868e0a0)" of type `GString'
Segmentation fault

There is a good possibility that the messages you're seeing there are related to an issue with a gtkrc file...

Are you using the Hardy repos or a third party repo?

If you are using the official Hardy packages you might want to try the awn-testing PPA.  [http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

It might also be useful to open a bug on [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn)  as the dev who tends to deal with the agnostic/xfce side of things doesn't actively monitor ubuntu forums.


Note:

It is possible to build with desktop agnostic options (for example for xfce4) though it is still somewhat experimental.  If you don't mind installing some gnome dependencies then the standard builds might be your best bet.  If you decide you're interested in that route I'd suggest posting a message on the forum ( [http://awn.planetblur.org](http://awn.planetblur.org) ) or drop by #awn on freenode.

---

### Post by nilsolaris on 2008-05-22
Alright well ill go give this a try... hopefully it works but now its starting to seem as multiple programs are doing the same thing, this including nicotine+, emerald as wellas a few others??

---

