---
title: "maintainer script logging"
date: 2010-07-31
forum: Packaging and Compiling Programs
---

### Post by ssalley on 2010-07-31
The package I help support (likewise-open) has a lot of things that can go wrong during install/uninstall/upgrades. I don't want to write a lot of stuff to stdout, because that would annoy/confuse/scare users and probably be against a packaging rule, somewhere.

But I'd like to log what is being executed and its output somewhere.  Are there any guidelines on what to print or where to log maintainer script happenings?

---

