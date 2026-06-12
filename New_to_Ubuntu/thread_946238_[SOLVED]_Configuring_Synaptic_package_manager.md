---
title: "[SOLVED] Configuring Synaptic package manager"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by mel37 on 2008-10-13
Hi 
When I try to open Synaptic package mgr, I get the following error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E:-cache>open()failed, please report.
I am newcomer and I would appreciate some help
Thanks
Mel

---

### Post by kosmiciatakuja on 2008-10-13
Do you know how to start a terminal console? Like gnome-terminal or something similar?

---

### Post by mel37 on 2008-10-13
> **kosmiciatakuja said:**
> Do you know how to start a terminal console? Like gnome-terminal or something similar?

yes I do.
mel

---

### Post by howefield on 2008-10-13
In your terminal type

```
sudo dpkg --configure -a
```

---

### Post by mel37 on 2008-10-13
ok thank you
mel

---

### Post by Sef on 2008-10-13
Moved to absolute beginners.

---

