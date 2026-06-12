---
title: "gtk c app in notification area"
date: 2007-07-10
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-07-10
Hi all,

Has anyone got any experience using the system noticiation area in gtk with C?

I'm doing a uTorrent clone and would like "minimise to system tray" functionality.

Alternatively, would would be a small gtk C app that has this functionality I could look at?

Cheers,
Alex

---

### Post by duff on 2007-07-10
check out GtkStatusIcon.  As for a small, real-world example, try zenity:

[http://svn.gnome.org/viewcvs/zenity/trunk/src/notification.c?view=markup](http://svn.gnome.org/viewcvs/zenity/trunk/src/notification.c?view=markup)

That'll even show you how to use libnotify.

---

### Post by AlexThomson_NZ on 2007-07-10
That's perfect!  Ta very much :D

---

