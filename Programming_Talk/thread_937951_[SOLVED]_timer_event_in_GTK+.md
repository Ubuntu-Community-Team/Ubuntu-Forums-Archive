---
title: "[SOLVED] timer event in GTK+"
date: 2008-10-04
forum: Programming Talk
---

### Post by pxhai on 2008-10-04
I need to use a timer event to execute an action at exact time intervals, like wxTimerEvent in wxWidgets, but the Gtk document didn't mention that. Can you tell me which event or signal is that?
Thanks,
pxhai

---

### Post by tigrezno on 2008-10-04
check for g_timeout_add

---

### Post by pxhai on 2008-10-04
Ok, thanks a lot. That's what I want.
Not yet familiar with the philosophy and naming of GTK :)

---

