---
title: "How to register global hotkey?"
date: 2011-05-19
forum: Programming Talk
---

### Post by hakermania on 2011-05-19
I am developing a Qt application and I want to register a global hotkey, it is something that cannot be done through the default Qt libraries.
I was told that Global Hotkeys is something system-dependent...

So, what I need is a Global Hotkey that exists and it is valid while my application is running (so to register the hotkey on start of the application and to unregister it on close)

Is this possible through a command or something?
Thanks a lot.

---

### Post by hakermania on 2011-05-20
bump

---

### Post by hakermania on 2011-05-21
bump

---

### Post by nvteighen on 2011-05-22
I guess that's DE-dependent. Check the libkdeui API for this, or maybe even Plasma. Sorry, I'm not a KDE user nor a KDE developer, but anyway it is there where I'd start looking at.

---

### Post by GeneralZod on 2011-05-22
If you go the libkde route, check out: [setGlobalShortcut(...)](http://api.kde.org/4.0-api/kdelibs-apidocs/kdeui/html/classKAction.html#a84b70169c75007569613ba14eb7d2ed7)

---

### Post by hakermania on 2011-05-22
lib**kde **?
are you sure this is gonna work in ubuntu :/ ?

---

### Post by nvteighen on 2011-05-22
> **hakermania said:**
> lib**kde **?
are you sure this is gonna work in ubuntu :/ ?

Of course, KDE is available in Ubuntu, not just Kubuntu. The difference between Ubuntu, Kubuntu and Xubuntu is just what the *default* DE is in each.

Now I realize that you might be trying something different: a Qt program that sets global hotkeys in GNOME. A quite unusual setup, but perfectly doable. If this is the case, you'll need libgnomeui. Maybe, you'll have to write some glue code that transforms Qt stuff into GLib stuff that libgnomeui may "understand".

If you go for Unity, the library would be libunity4 (or whatever its name is...).

Here comes the full explanation of what the underlying concept is.

Global hotkeys is something that is not a job for GUI toolkits (Qt, GTK+). GUI toolkits just provide an easier object-based way to "draw" UIs into the screen, on top of the X API. That's why a Qt program can work e.g. in the GNUStep DE, unless the program needs some DE-specific functionality of course.

Hotkeys aren't really managed by the system either. You have to realize that in GNU/Linux the GUI is a completely secondary component of the system. There are very few components that are "system-dependent" in GNU/Linux: the kernel, the C and C++ Standard Library, the GNU utils, the BSD utils, the POSIX API. The *only* hotkeys managed by the system are the so-called "Magic SysRq" combinations, which are managed by the kernel and meant to be used in extreme system crashes ([http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key))

A DE is not only a collection of programs but also manages the "general" user interface. I assume global hotkeys to be managed there because it's the kind of feature that is application-independent but nevertheless part of the GUI (therefore, not system-dependent). Architecturally, the only place I can imagine this to be set is the in DE. Therefore, you have to interface with the DE, preferrably through the API.

---

