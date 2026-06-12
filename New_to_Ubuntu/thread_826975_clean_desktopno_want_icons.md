---
title: "clean desktop/no want icons"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-12
so unlike in windows where the desktop provides shortcuts to stuff via icons that if erased do not demolish the entire application it represents, unlike here in ubuntu where i just went to trash a shortcut and the whole package went with it.  My question is, why?  and more importantly how do I clean my desktop (i hate icons in the workspace) w/out dumping the application?

---

### Post by sdennie on 2008-06-12
Are you sure that the whole package went with it?  It's possible that you just can't find the package anymore.  Unless you erased a folder that an application lived in or the actual application was sitting on your desktop, it's not possible for a symlink removal to also remove the application.

Also, to remove all desktop icons, you can hit Alt-F2 and type gconf-editor.  Navigate to /apps/nautilus and in the desktop section uncheck all the show_whatever options.  Also in the preferences section uncheck the show_desktop option.  That will prevent any icons from showing up on your desktop.

---

### Post by ukripper on 2008-06-12
> **adamogardner said:**
> so unlike in windows where the desktop provides shortcuts to stuff via icons that if erased do not demolish the entire application it represents, unlike here in ubuntu where i just went to trash a shortcut and the whole package went with it.  My question is, why?  and more importantly how do I clean my desktop (i hate icons in the workspace) w/out dumping the application?

Your shortcut/link was hardlinked to the package that is why it went to trash.

Make sure you right click on app and then Add to desktop that will create symbolic link not a hardlink. For folder right click and "Make link" to create symbolic link

---

### Post by adamogardner on 2008-06-12
there is no option remotely similar to "show_desktop option"  there is only one option under nautilus (i don't recall but it was wrong thing).  So in taking uk's advice I right clicked on apps (in the gconf-editor menu - thats where you meant right?) but that did nothing at all.

---

### Post by sdennie on 2008-06-12
This is what you should be seeing in gconf-editor.

---

### Post by nhsbgeek2011 on 2008-06-12
[http://s6.gladiatus.us/game/c.php?uid=42772](http://s6.gladiatus.us/game/c.php?uid=42772)

---

### Post by kansasnoob on 2008-06-12
I'm still learning the desktop myself (gnome) and I've found this invaluable:

[http://library.gnome.org/users/user-guide/stable/prefs.html](http://library.gnome.org/users/user-guide/stable/prefs.html)

---

### Post by adamogardner on 2008-06-12
ok  i did that but now i have the same problem i had before which is that my raindrop viual effect stops displaying on the desktop and only displlays over menus and windows.  this means the icons are there   theey are just masked over.  this is not what i want.  perhaps i just installed them incorrectly.

---

### Post by sdennie on 2008-06-12
I'm pretty sure that's a bug with the raindrop effect.  It's an incredibly buggy plugin.

---

