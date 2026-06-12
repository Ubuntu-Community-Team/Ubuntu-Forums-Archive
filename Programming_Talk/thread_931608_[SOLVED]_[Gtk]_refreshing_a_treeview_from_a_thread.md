---
title: "[SOLVED] [Gtk] refreshing a treeview from a thread"
date: 2008-09-27
forum: Programming Talk
---

### Post by tigrezno on 2008-09-27
Hi, i'm updating a tree model within a thread.
My problem is that i can only see the result if I move my mouse over the window. If I don't touch the window, nothing got refreshed.

Do you know how can i force it after each insertion on the model?

Thanks.

---

### Post by gomputor on 2008-09-27
It would be better to mention the language that it is written, and if you could provide some code.

---

### Post by tigrezno on 2008-09-28
I solved it, after so much reading on the web i find that you "must not" refresh any widget from a thread that didn't run the gtk main loop.

---

