---
title: "Slow Gio::FileMonitor"
date: 2010-03-12
forum: Programming Talk
---

### Post by kahumba on 2010-03-12
Hi,
I noticed that when using the Gio::FileMonitor it only reports the changes after like a second. This makes my application feel sluggish.
set_rate_limit() doesn't do the trick.

Does anyone know any workaround and if none, what API should I learn to get around it? If any, can I also have a link to a tutorial please? I only need it running on Ubuntu (not windows nor mac).

Btw, it's not Ubuntu's fault, mostly likely it's some part of Gnome to blame, cause I have Java 7 on Ubuntu which allows for (native) file monitoring and the changes are reported instantly.

---

### Post by SledgeHammer_999 on 2010-03-12
If you're going to use it only on linux then use [inotify](http://en.wikipedia.org/wiki/Inotify) directly. Sorry I don't have any exprerience with Gio.

---

### Post by SledgeHammer_999 on 2010-03-12
EDIT: Not Gnome's fault. Gtk's fault. And as I understand Gio is a somewhat newly introduced module. Maybe you should file a bug or ask a queston on the mailing lists(or on IRC).

---

### Post by kahumba on 2010-03-12
Uh, thanks a lot, I'll have a look at inotify and if anything, report back.

Edit (in May): inotify solves the problem - it reports changes instantly. Hence it turns out only Gio::FileMonitor is to blame, not Linux nor the Gtkmm programmer.

---

