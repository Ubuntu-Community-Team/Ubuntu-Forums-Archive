---
title: "How to modify rules-file if source is in ckit/ckit-0.1/src/"
date: 2008-11-11
forum: Packaging and Compiling Programs
---

### Post by gercokees on 2008-11-11
Hi,

My source has its source in: ckit/ckit-0.1/src/
I changed one line in my rulesfile:
build:
        ./configure --prefix=/usr

to
build:
        .src/configure --prefix=/usr

To let the dpkg-buildbackage -rfakeroot command find the configure file.
Now it starts to complain that no clean-up rule could be found. How do I have to change the rules file to solve that problem?
Thanx in advance...

---

