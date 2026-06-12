---
title: "Have pbuilder build a debugging package"
date: 2010-10-08
forum: Packaging and Compiling Programs
---

### Post by SoftwareExplorer on 2010-10-08
I did a google search, but didn't get any promising links. How can I get pbuilder to not just build the normal .deb but also a -dbg deb so I can use a debugger? I'm working on the gtk2-engines-murrine package, so I'm pretty sure it's already packaged correctly to have a -dbg package made. I just don't know how to trigger it to do that.

---

### Post by MadCow108 on 2010-10-10
providing the package is well behaved adding nostrip (and possibly noopt) to DEB_BUILD_OPTIONS environment variable should suffice

[http://www.debian.org/doc/debian-policy/ch-source.html#s-debianrules-options](http://www.debian.org/doc/debian-policy/ch-source.html#s-debianrules-options)

---

