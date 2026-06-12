---
title: "Trigger run-dialog?"
date: 2006-05-14
forum: Programming Talk
---

### Post by dabear on 2006-05-14
When pressing alt + F2, a run-dialog appears. How can I start this from an application I'm developing in GNOME? I am using python, but it would be nice if some one knows how I could do it in c++ too.

---

### Post by RavenOfOdin on 2006-05-14
[QUOTE=dabear]When pressing alt + F2, a run-dialog appears. How can I start this from an application I'm developing in GNOME? I am using python, but it would be nice if some one knows how I could do it in c++ too.[/QUOTE]

I think that would best be done via GtkDialog or GtkMenu.

Are you using libglade?

---

