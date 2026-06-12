---
title: "Ruby Upgrade Without Damaging Dependencies."
date: 2013-03-05
forum: Programming Talk
---

### Post by DiagonalArg on 2013-03-05
This is (hopefully) a basic question.  I have ruby 1.8 installed on Ubuntu 12.04.  This was an automatic install as the result of some dependency.  I now need Ruby 1.9.3 for a class.  Running:
[FONT=Ubuntu Mono]
apt-cache rdepends ruby1.8 

produces a long list of packages.  [/FONT]How do I install Ruby 1.9.3 without damaging packages that might depend on 1.8?

Thx
/DA

---

### Post by tgalati4 on 2013-03-05
Depending on what service you need to run, I would install a [http://bitnami.org](http://bitnami.org) stack.  This method installs a service (with all of its static dependencies) in a single directory, and it doesn't interfere with apt or repositories, or your current development environment.  If you need both ruby1.8 and 1.9 for code development, then you have a problem.  So which ruby is needed for development (actual coding by you) and which ruby is needed to run a service (no coding, just configuration)?

And you are correct both ruby1.8 and 1.9 have huge rdepends lists.  I think 12.10 has 1.9.1 as a base ruby version.  I think there is a way to have them both installed, side-by-side, with symlinks and pointers, and I did that a few years ago for some Tracks development work but I ended up doing a bitnami stack install because it was cleaner and less of a dependency mess.

---

### Post by DiagonalArg on 2013-03-06
Thanks tgalati4! Great advice.

---

