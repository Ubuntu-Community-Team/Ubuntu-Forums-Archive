---
title: "Handling shutdown signal in Python"
date: 2014-08-28
forum: Programming Talk
---

### Post by hamiljf on 2014-08-28
One can only set a signal handler in the main thread in Python.  However, tkinter grabs the main thread.  Is there any experience on the best way to program this.  I'm planning to set the SIGTERM handler in the main thread and then start tkinter on the assumption that the mainloop() will be interrupted.  Testing may be a bit tricky.

---

