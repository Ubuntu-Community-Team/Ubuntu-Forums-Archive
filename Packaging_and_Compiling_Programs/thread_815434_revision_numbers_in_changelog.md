---
title: "revision numbers in changelog"
date: 2008-06-01
forum: Packaging and Compiling Programs
---

### Post by duffrecords on 2008-06-01
I'm packaging Ardour version 2.4.1 for Hardy Heron using the [Updating an Ubuntu Package]("https://wiki.ubuntu.com/PackagingGuide/Recipes/PackageUpdate?highlight=(CategoryPackagingGuideRecipe)") guide but I'm a little confused as to what's the correct formatting for the version number.  I've downloaded the old source using```
apt-get source ardour
```and the most recent version via```
wget http://ardour.org/files/releases/ardour-2.4.1.tar.bz2
```

So when I edit the changelog, would the following version be correct?```
ardour (1:2.4.1-1ubuntu1) hardy; urgency=low
```I'm not sure whether any changes have been made by Ubuntu because the previous entry in the changelog says```
ardour (1:2.3.1-1) unstable; urgency=low
```

Thanks in advance for any assistance.  I'd really like to contribute to the community, especially in the realm of audio production.

---

### Post by duffrecords on 2008-06-01
For now I chose 1:2.4.1-1ubuntu1, but when I run pbuilder, I see the following messages (summarized):```
The following packages are BROKEN:
  pbuilder-satisfydepends-dummy
The following packages have unmet dependencies:
  pbuilder-satisfydepends-dummy: Depends: ladspa-sdk (>= 1.1-2) which is a virtual package.
                                 Depends: libjack-dev which is a virtual package.
                                 Depends: liblo0-dev which is a virtual package.
                                 Depends: liblrdf0-dev (>= 0.3.1-4) which is a virtual package.
                                 Depends: libsoundtouch1-dev which is a virtual package.
The following packages will be automatically REMOVED:
  pbuilder-satisfydepends-dummy
Aptitude couldn't satisfy the build dependencies
E: pbuilder-satisfydepends failed.
```
I have all of those libraries (libjack-dev, liblo0-dev, etc.) installed on my machine.  Does this mean I need to install them in the chroot cleanroom as well?  How do I do that?

---

### Post by duffrecords on 2008-06-01
:? I guess I just answered my own question.  I needed to add [Universe support]("https://wiki.ubuntu.com/PbuilderHowto#head-5e61fa0f52f7f2442fb20f074813bd691744460b") within the cleanroom in order to satisfy those dependencies.  The package is now being built and if all goes well and someone lets me know if I used the correct version format (1:2.4.1-1ubuntu1) I'll try to submit it to the hardy repository.

---

