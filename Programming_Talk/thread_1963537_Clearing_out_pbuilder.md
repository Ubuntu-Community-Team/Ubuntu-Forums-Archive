---
title: "Clearing out pbuilder"
date: 2012-04-22
forum: Programming Talk
---

### Post by WebDrake on 2012-04-22
Hello all,

I was having a play with the how-to-build-a-deb-package-on-Launchpad instructions here:
[https://help.launchpad.net/Packaging/SourceBuilds/GettingStarted](https://help.launchpad.net/Packaging/SourceBuilds/GettingStarted)

As per the instructions I installed pbuilder and created a chroot environment.  Lots of packages were downloaded in the process.  But WHERE did pbuilder install them?  I cannot find where they are located.

Further -- how do I completely uninstall all of this and completely clear my system of all pbuilder-related stuff?

Thanks very much!

---

### Post by MadCow108 on 2012-04-22
by default they should be in /var/cache/pbuilder/base.tgz
you can change it with the --basetgz flag or BASETGZ environment variable (e.g. from .pbuilderrc)

---

### Post by WebDrake on 2012-04-22
OK, cool.  So deleting the /var/cache/pbuilder dir and all of its contents should clear out all of this stuff from my system?

---

### Post by MadCow108 on 2012-04-23
yes

---

### Post by WebDrake on 2012-04-27
Thanks! :-)

---

