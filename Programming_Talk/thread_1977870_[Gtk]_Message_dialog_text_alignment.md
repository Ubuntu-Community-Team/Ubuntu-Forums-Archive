---
title: "[Gtk] Message dialog text alignment"
date: 2012-05-10
forum: Programming Talk
---

### Post by t1497f35 on 2012-05-10
Hi,
The text in the gtk message dialog is either higher (set_message func, see screenshot) or below (set_secondary_text func) the left icon.

How can I make the text appear vertically in the middle of the dialog **at the same level as the left icon**?

---

### Post by r-senior on 2012-05-11
If you want to change the layout of a message alert dialog, you need to create your own dialog window and lay out the controls within it.

But ...

You would then be diverging from the standard alert dialog layout and your application would be inconsistent with other GTK applications. The standard message dialogs follow the GNOME Human Interface Guidelines:

[http://developer.gnome.org/hig-book/3.0/windows-alert.html.en#alert-spacing](http://developer.gnome.org/hig-book/3.0/windows-alert.html.en#alert-spacing)

---

