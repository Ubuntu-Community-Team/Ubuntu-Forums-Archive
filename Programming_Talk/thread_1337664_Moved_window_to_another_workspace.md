---
title: "Moved window to another workspace"
date: 2009-11-25
forum: Programming Talk
---

### Post by Wiebert on 2009-11-25
Hi,

The normal auto start on login doesnt allow to specify on what workspace which windows should start.
Is it possible to move the windows via a API / terminal command ? (something that works with Python would be nice).

Thanks.

---

### Post by kaibob on 2009-11-25
> **Wiebert said:**
> Hi,

The normal auto start on login doesnt allow to specify on what workspace which windows should start.
Is it possible to move the windows via a API / terminal command ? (something that works with Python would be nice).

Thanks.

I don't have a good answer to your question. But, if nothing else come's up, you may want to look at the xdotool command-line utility. It has a set_desktop_for_window option that moves a window to a different desktop. It's not installed by default but is in the repo's.

---

### Post by diesch on 2009-11-25
*wmctrl* (not installed by default) lets you do things like that from the command line.

If you want some windows to always start on a specific workspace have a look at *devilspie* (not installed by default).

---

