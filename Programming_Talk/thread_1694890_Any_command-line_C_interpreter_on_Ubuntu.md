---
title: "Any command-line C interpreter on Ubuntu?"
date: 2011-02-25
forum: Programming Talk
---

### Post by Zacinfinite on 2011-02-25
Is there anything like C interpreter on Ubuntu?
Python interpreter makes it really easy to test and experiment codes. So i was wondering if there is any C interpreters available for ubuntu.

---

### Post by schauerlich on 2011-02-25
C is generally a compiled language, but interpreters do exist.

[http://en.wikipedia.org/wiki/Ch_interpreter](http://en.wikipedia.org/wiki/Ch_interpreter)

---

### Post by MadCow108 on 2011-02-25
there is CINT
[http://root.cern.ch/drupal/content/cint](http://root.cern.ch/drupal/content/cint)

which is even a C++ interpreter.
it is included in the package root-system. But it is very outdated, better grab it from the main site

there is also some work on a new version based on llvm:
[http://indico.cern.ch/materialDisplay.py?contribId=3&materialId=slides&confId=71078](http://indico.cern.ch/materialDisplay.py?contribId=3&materialId=slides&confId=71078)
but I'm not sure how far this is.

---

### Post by foxmuldr on 2011-02-25
> **Zacinfinite said:**
> Is there anything like C interpreter on Ubuntu?
Python interpreter makes it really easy to test and experiment codes. So i was wondering if there is any C interpreters available for ubuntu.

The TinyCC (Tiny C Compiler) can be run from the command line.  It can be used in shell scripts, etc.  It's very fast.

---

