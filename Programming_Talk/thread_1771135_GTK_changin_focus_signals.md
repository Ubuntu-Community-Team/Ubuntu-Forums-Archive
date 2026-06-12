---
title: "GTK changin focus signals"
date: 2011-05-30
forum: Programming Talk
---

### Post by hapyfishrmn on 2011-05-30
Hey all,
 I am using C & GTK+ and have 6 GTKEntry text field on a window and I want to click a button to change the focus from 1 to the other in order. I dont think I need to create a tab ordered list, because the order works when using the keyboard TAB. I do my button to function exactly like the TAB does on the keyboard. I'm just not finding the right place to look.


Totally unrelated, Im also trying to make the scrollbar wider for a GTK Tree view using a scrollwindow. Is this possible in the GTK Api's?

Any help would be appreciative.

Thanks

---

### Post by Petrolea on 2011-05-30
> **hapyfishrmn said:**
> Hey all,
 I am using C & GTK+ and have 6 GTKEntry text field on a window and I want to click a button to change the focus from 1 to the other in order. I dont think I need to create a tab ordered list, because the order works when using the keyboard TAB. I do my button to function exactly like the TAB does on the keyboard. I'm just not finding the right place to look.


Totally unrelated, Im also trying to make the scrollbar wider for a GTK Tree view using a scrollwindow. Is this possible in the GTK Api's?

Any help would be appreciative.

Thanks

When you press TAB you change focus. Take a look into changing focus in GTK apps (it's really easy :)).

---

### Post by JupiterV2 on 2011-05-30
> **hapyfishrmn said:**
> Hey all,
 I am using C & GTK+ and have 6 GTKEntry text field on a window and I want to click a button to change the focus from 1 to the other in order. I dont think I need to create a tab ordered list, because the order works when using the keyboard TAB. I do my button to function exactly like the TAB does on the keyboard. I'm just not finding the right place to look.

Use gtk_widget_grab_focus().

> Totally unrelated, Im also trying to make the scrollbar wider for a GTK Tree view using a scrollwindow. Is this possible in the GTK Api's?

Any help would be appreciative.

Thanks

The width of a scrollbar is set by the theme set by the user. You can't control this within GTK+.

---

### Post by SledgeHammer_999 on 2011-05-30
I think he means "How do I discover the focus **order** like TAB does."

EDIT: I think I found the answer. Use [gtk_widget_child_focus()](http://developer.gnome.org/gtk/stable/GtkWidget.html#gtk-widget-child-focus). As GtkWidget specify the container and as GtkDirectionType use GTK_DIR_TAB_FORWARD.

---

### Post by hapyfishrmn on 2011-06-01
Yes sledgehammer your right but when I use that I keep getting FALSE returned. Do I need to set focus again before I call that function?

---

