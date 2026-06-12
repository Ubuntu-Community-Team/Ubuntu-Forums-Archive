---
title: "How to understand if a package is pre-installed or not."
date: 2011-01-15
forum: Programming Talk
---

### Post by hakermania on 2011-01-15
I need to know this, because I am making a program and so I need to have the dependencies...
E.g. Is mencoder pre-installed or I once installed in my system being a dependency of an other application?
That's the question.

---

### Post by MadCow108 on 2011-01-15
you can look at the dependencies of ubuntu-desktop (or ubuntu-minimal) package.
You probably want to install apt-rdepends to do the recursion of apt-cache depends for you
or do apt-cache rdeps needed-package and search for ubuntu-desktop

mencoder is so far I know not installed by default.

Why do you need to know this? package managemers exist so you don't have to worry about this.

for non-packaged managed distributions you may want to look at the set of applications a lsb certified distro must provide. Its somewhere on this page, can't remember where
[http://www.linuxfoundation.org/collaborate/workgroups/lsb](http://www.linuxfoundation.org/collaborate/workgroups/lsb)

---

