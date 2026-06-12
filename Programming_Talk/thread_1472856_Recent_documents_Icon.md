---
title: "Recent documents Icon?"
date: 2010-05-04
forum: Programming Talk
---

### Post by louis--taylor on 2010-05-04
Hi!
Does anyone know if this icon can be used as a stock icon in gtk?
If so, what is the name of it?
If not, where can I get it from?
[IMG]http://dl.dropbox.com/u/3746044/clocky_thing.png[/IMG]

Thank you!

---

### Post by cszikszoy on 2010-05-04
Yes, it is a GTK stock icon, the action is "document-open-recent", the place is "folder-recent".  Note that some icon sets might not have "folder-recent", so if it doesn't fallback to the other.

---

### Post by louis--taylor on 2010-05-05
Thank you very much! :)

---

### Post by louis--taylor on 2010-05-06
Any idea how I would use this in a menu?
I have been using gtk.ImageMenuItem(gtk.STOCK_OPEN) (or any other stock icon) for my image menus, but the icon I want to use is not in the list of standard icons. I would like to avoid using a custom menu item, as this hinders localization and themeability.

Thank you!

---

