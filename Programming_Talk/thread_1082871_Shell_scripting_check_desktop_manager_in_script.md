---
title: "Shell scripting: check desktop manager in script"
date: 2009-02-28
forum: Programming Talk
---

### Post by lilbill on 2009-02-28
I'd like to know if it is possible to check which desktop manager, KDE or GNOME is running when a certain script I'm writing runs.  This is so that different things execute depending on the DM.

Does anyone know how to do this?

---

### Post by unoodles on 2009-02-28
try the $DESKTOP_SESSION environment variable.

---

### Post by lilbill on 2009-02-28
BEAUTIFUL thanks a bunch...problem solved!  Thanks again!

---

