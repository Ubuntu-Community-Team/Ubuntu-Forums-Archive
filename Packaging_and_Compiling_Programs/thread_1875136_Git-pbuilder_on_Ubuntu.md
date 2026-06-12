---
title: "Git-pbuilder on Ubuntu"
date: 2011-11-04
forum: Packaging and Compiling Programs
---

### Post by dshh2011 on 2011-11-04
Hi guys,

I can't find out the reason why *git-buildpackage* always calls *debuild* on my Oneiric although *git-pbuilder* is given everywhere in the configuration files as builder:

/etc/git-buildpackage/gbp.conf:
     [DEFAULT]
     # the default build command:
     #builder = debuild -i -I
     # the default clean command:

~/.gbp.conf:
     # the default build command:
     # builder = debuild -i -I
     builder= git-pbuilder

in my *debian/gbp.conf* there isn't any additional builder option at all. Trying to run *git-buildpackage* it of course goes like:

<cut>
$ git-buildpackage 
dpkg-checkbuilddeps: Unmet build dependencies: libpoppler-dev (>= 0.7.3) libdjvulibre-dev (>= 3.5.23-6) libpstreams-dev libgraphicsmagick++1-dev libxslt1-dev
debuild: fatal error at line 1312:
You do not appear to have all build dependencies properly met.
You can use mk-build-deps to generate a dummy package which
Depends on all the required packages, or you can install them
manually using dpkg or apt using the error messages just above
this message.
gbp:error: debuild clean returned 1
gbp:error: Couldn't run 'debuild clean'
</cut>
(that's a Debian packet so of course the deps aren't fulfilles).

Any pointer appreciated,
DS

---

### Post by dshh2011 on 2011-11-04
For the cleaner, the line "debuild -d clean" must be given to the gbp.conf to prevent the invocation of dpkg-checkbuilddeps (which of course of Ubuntu gives errors).

---

### Post by SevenMachines on 2011-11-04
Missing the section header
~/.gbp.conf
```
[DEFAULT]
builder= git-pbuilder
```Or is it already solved

---

