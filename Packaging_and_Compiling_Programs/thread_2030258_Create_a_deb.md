---
title: "Create a deb"
date: 2012-07-20
forum: Packaging and Compiling Programs
---

### Post by bilboubu on 2012-07-20
I am trying to use these intstructions to create an installer:

[http://forum.xbmc.org/showthread.php?tid=133917&pid=1144451#pid1144451](http://forum.xbmc.org/showthread.php?tid=133917&pid=1144451#pid1144451)

but I am getting the below error. Is there something in particular I need to do or some other way to install?


billy@HTPC:~/tvh-adamsutton$ AUTOBUILD_CONFIGURE_EXTRA= ./Autobuild.sh -t precise-i386
fatal: No names found, cannot describe anything.
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): -D_FORTIFY_SOURCE=2
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions -Wl,-z,relro
parsechangelog/debian: warning: debian/changelog(l1): badly formatted heading line
LINE: tvheadend () unstable; urgency=low
parsechangelog/debian: warning: debian/changelog(l2): found blank line where expected first heading
parsechangelog/debian: warning: debian/changelog(l3): found change data where expected first heading
LINE: * The full changelog can be found at
parsechangelog/debian: error: Can't call method "as_string" on an undefined value at /usr/share/perl5/Dpkg/Changelog.pm line 250, <STDIN> line 6.

dpkg-buildpackage: error: changelog parser /usr/lib/dpkg/parsechangelog/debian gave error exit status 255
billy@HTPC:~/tvh-adamsutton$

---

### Post by thatguruguy on 2012-07-20
Looks like a broken changelog in the package you're tying to make into a .deb.

You might consider either using the ppa mentioned in the post you've linked, or posting your question in that thread.

---

### Post by bilboubu on 2012-07-20
That ppa doesn't have the version I need.

---

### Post by oldos2er on 2012-07-20
Moved to Packaging and Compiling Programs.

---

### Post by SevenMachines on 2012-07-21
This automatic method of assigning a version from git is failing leaving a blank version in the generated changelog, which causes the debuild to fail
Autobuild/debian.sh:```
VER=`git describe | sed "s/\([0-9]*\)\.\([0-9]*\)-\([0-9]*\)-.*/\1.\2.\3/"`
```
Think the author or you would need to tag some new commits for the above to work.   For the moment you could just change it to assign a version of somekind, VER=0.1 
or something.

---

### Post by bilboubu on 2012-07-22
This worked, thank you so much.

---

