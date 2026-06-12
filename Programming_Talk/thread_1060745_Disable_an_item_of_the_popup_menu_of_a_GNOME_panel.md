---
title: "Disable an item of the popup menu of a GNOME panel applet"
date: 2009-02-05
forum: Programming Talk
---

### Post by mrShadow on 2009-02-05
Hi. I'm writing a GNOME panel applet and want to disable a menu item in run-time. How can I do that?

I already googled it and asked it in irc.gnome.org#gtk+, but got no replies. I also asked it in Gtk+ mailing list a week ago, but the message is still in pre-moderation, and I don't want to wait any more.

That would be great if I could get a GtkMenu corresponding to the popup menu. I tried gtk_menu_get_for_attach_widget() passing my PanelApplet object, but it returned an empty list.

There is also a method of PanelApplet called [panel_applet_get_popup_component]("http://library.gnome.org/devel/panel-applet/stable/PanelApplet.html#panel-applet-get-popup-component"), but I have no idea how to use the object returned.

I actually use PyGTK, but a GTK+ solution will be greatly appreciated too.

*Sorry for my English.*

---

### Post by mrShadow on 2009-02-06
Anybody?

---

### Post by Vadi on 2009-02-08
I'm interested in finding this out too. He meant the menu that you get when you right-click on an applet

---

