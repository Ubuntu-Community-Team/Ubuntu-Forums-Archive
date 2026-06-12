---
title: "Is Ubuntu having GTK Runtimes (lib)?"
date: 2007-11-01
forum: Programming Talk
---

### Post by legends2k on 2007-11-01
If I write an application using GTK+-2.0 in pure C, will the compiled output run on any other system with where **ONLY** Ubuntu is installed, with default options and no additional updates done, in 7.10.

Simply put, from scratch in a system, if Ubuntu 7.10 is installed, will it have GTK 2.0 or GTK+ libs, so that my app. will run with any additional libs??

---

### Post by tageiru on 2007-11-01
Yes.

GTK maintains ABI compatability throughout x.x releases, so bugfix updates won't interfere with your app.

---

### Post by legends2k on 2007-11-01
Thanks for the info man.. I was worried!

---

