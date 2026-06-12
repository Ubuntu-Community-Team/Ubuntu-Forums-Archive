---
title: "kdebase-dev Dependency Wait"
date: 2009-06-29
forum: Packaging and Compiling Programs
---

### Post by ace214 on 2009-06-29
I tried packaging a program for Karmic on my PPA and got a message about a dependency wait on the "kdebase-dev" package. I noticed that this package does not exist past Jaunty. Is there an easy way to figure out what to replace this with.

Note that I am simply updating the package- I'm not the original packager so I don't know the exact purpose of kdebase-dev, but I assume that the dependency is there for the sake of dolphin and other libs.

[A summary of the builds I am referring to.]("https://launchpad.net/~jonarnoldsemail/+archive/ppa/+builds?build_text=&build_state=depwait")

ADD: If I package it without that dependency, then none of the icons in any of the toolbars show up...

---

