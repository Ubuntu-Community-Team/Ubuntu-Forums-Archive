---
title: "gtk# toolbar problem"
date: 2008-09-29
forum: Programming Talk
---

### Post by lviggiani on 2008-09-29
Hi,
I'm writing a program in c# (mono with gtk#).
I'm wondering how to add a button or a custom image / animation to a tool bar and have it aligned to the right. For example see the toolbar of nautilus: the gnome logo (see attachment).

Thanks in advance!

---

### Post by bruce89 on 2008-09-29
> **lviggiani said:**
> Hi,
I'm writing a program in c# (mono with gtk#).
I'm wondering how to add a button or a custom image / animation to a tool bar and have it aligned to the right. For example see the toolbar of nautilus: the gnome logo (see attachment).

Thanks in advance!

Don't hijack threads like this.

Anyway, use a Gtk.SeparatorToolItem, and set "draw" to false, and "expand" to true.

---

### Post by Joeb454 on 2008-09-29
I've moved the post(s) to a new thread.

bruce89 is right however, please don't hijack threads like that, it'd be much easier to create a new thread (especially as the last activity from the original was nearly a year ago).

---

