---
title: "Global key shortcuts with Qt5"
date: 2013-08-30
forum: Programming Talk
---

### Post by kangaba on 2013-08-30
Hi,
[QxtGlobalShortcut]("http://libqxt.bitbucket.org/doc/tip/qxtglobalshortcut.html") doesn't work with qt5, any suggestions what else could be used?

Using qt 5.1.1 amd64 on Ubuntu 13.04 amd64.

---

### Post by Vaphell on 2013-08-30
maybe this?
[http://qt-project.org/doc/qt-5.1/qtwidgets/qshortcut.html](http://qt-project.org/doc/qt-5.1/qtwidgets/qshortcut.html)
setContext( Qt::ApplicationShortcut )

edit: oh you mean global global shortcuts. Isn't that the job of the OS anyway?

---

### Post by kangaba on 2013-08-31
Thanks, it's a simple task, just like the system tray is an OS job but the toolkit supports the latter, IMO so should be the global shortcut. Anyway, I'm doing a simple audio player and without global shortcuts (to be able press the play/pause/etc key on your keyboard no matter what app has focus) the player feels too limited even for a basic audio player.
I'd search for an X11 solution but it's so dusty (old) and complicated that I'd only go for a readily working example.

---

