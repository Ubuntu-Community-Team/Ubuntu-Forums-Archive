---
title: "Launchpad autobuilder fails building linux 3.0.0 on Ubuntu 10.04 LTS"
date: 2011-08-31
forum: Packaging and Compiling Programs
---

### Post by ptn107 on 2011-08-31
Basically Linux 3.0.0 requires dpkg (>= 1.16.0~ubuntu4) on the lucid build machines but lucid uses dpkg 1.15.5.6ubuntu4.5.  Is there any way to fake the build machines into doing this or can I just remove the '(>= 1.16.0~ubuntu4)' from the control file?  How critical is it for the package to have this specific version in the control file?  Would I have to backport dpkg 1.16.0.3ubuntu3 to lucid and upload that as well?  Help!

---

### Post by MadCow108 on 2011-08-31
1.16.0~ is the version adding multiarch support
The linux 3.0.0 packages probably uses these features else it would not have been added to the control file.

=> you need to backport dpkg or remove the use of these features from the kernel package. Both probably not easy tasks. The latter could the simpler one.
Maybe ask the kernel team how feasible this is or if they have plans to do that themselves at some point.

---

