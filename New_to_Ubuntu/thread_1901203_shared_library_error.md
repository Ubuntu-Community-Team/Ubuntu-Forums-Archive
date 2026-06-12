---
title: "shared library error"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by Nitish.B on 2011-12-28
Hello everyone,
when i was trying to install glib2.30.0 I encountered this error:
/usr/local/bin/msgfmt: error while loading shared libraries: libgettextsrc-0.18.1.so: cannot open shared object file: No such file or directory
Please help.
Thanks in advance.

---

### Post by Perfect Storm on 2011-12-28
Which application are you trying to run? Have you checked if it's available through Ubuntu Software Center?


Try **ldd** the binary via the terminal.

---

