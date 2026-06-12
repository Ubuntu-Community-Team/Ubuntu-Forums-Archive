---
title: "Wrong Emacs in info dir"
date: 2007-09-09
forum: Programming Talk
---

### Post by siepo on 2007-09-09
I replaced Emacs21 first with Emacs-snapshot, then with emacs22. Now info lists entries for emacs-21 and for emacs-snapshot, which are no longer there, but not for emacs-22. There is a directory /usr/share/info/emacs22 with a lot of stuff in it but no dir file. `dpkg-reconfigure emacs22-common' does not fix this. Is this a bug? Is there a practical way to generate this file or to solve the problem some other way?

---

### Post by siepo on 2007-09-09
As a quick fix, I made an emacs-snapshot symlink for emacs22 but of course this is just a temporary workaround.

---

