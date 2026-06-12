---
title: "gcc 4.5 won't compile my programs which uses MPL from boost 1.42"
date: 2010-12-16
forum: Packaging and Compiling Programs
---

### Post by Chaos A.D. on 2010-12-16
Hello all, after switching to boost 1.42, my programs fails to comiple because of error in boost/mpl/aux_/template_arity.hpp and it's preprocessed sibling.

Several months ago I already rejected the idea of switching on 1.42 from 1.40 because of this error, despite this bug was already fixed in boost svn (or git, I don't remember what these guys using).

I just wanted to ask - where I should post bugs, and what is the probability of including this fix in the official ubuntu package repository?

---

### Post by MadCow108 on 2010-12-16
chances of getting a patch in maverick are pretty slim as the supported compiler of that release is 4.4

4.5 will be default for natty but according to a discussion on the mailing list it seems the decision was to keep the boost version in sync with debian => 1.42 in natty
[https://lists.ubuntu.com/archives/ubuntu-devel/2010-October/031848.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-October/031848.html)

file a report of your bug against the apropriate boost package at launchpad and mention where the fix can be found:
[https://launchpad.net/ubuntu/+source/boost1.42](https://launchpad.net/ubuntu/+source/boost1.42)

If the bug is considered serious enough we might get a patched boost for natty

---

### Post by Chaos A.D. on 2010-12-16
Thanks a lot, MadCow!

---

