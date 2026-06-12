---
title: "[Gtk] Alt-Tab hi-res icons work only for .desktop files?"
date: 2012-09-05
forum: Programming Talk
---

### Post by bird1500 on 2012-09-05
Hi,
In the Alt+Tab list of currently running app icons a hi-res version of an app icon is only displayed if the app has an associated .desktop file (which specifies the icon, say, "icon-name").

The older/general way of setting the icon:
[PHP]
myWindow->set_icon(Gtk::IconTheme::get_default()->load_icon("icon-name",
        128, Gtk::ICON_LOOKUP_USE_BUILTIN));
[/PHP]displays a lower-res (blurred) icon in the Alt-Tab menu regardless of the resolution of the loaded icon (in this case a 128x128 icon). Can it be fixed other than with a .desktop file? Is it a Unity/gtk bug or a policy?

---

### Post by bird1500 on 2012-09-05
Here's 2 screenshots, one without a desktop file, and one with.

---

