---
title: "Building boxee from source"
date: 2011-03-15
forum: Packaging and Compiling Programs
---

### Post by mrplow on 2011-03-15
My goal is to get the newest version boxee to build from source, hopefully creating a usefull dsc file for easy building.
Now there is no ubuntu source for this, just what boxee provides inside their massive 216mb source archive including a bootstrap file, and make. There is also a install-pkg file which lists a bunch of build dependencies I guess.
Now I can manage to get it to build, kinda, the program still doesn't work perfect but first off I'd like to get the build environment setup nicely.
I'd like to use pbuild to make sure I've got the build dependencies setup properly. Idealy I'd have this setup as a launchpad ppa once I've got it building nicely. Any help would be appreciated.

---

### Post by Ibidem on 2011-03-17
[http://forums.boxee.tv/showthread.php?t=13206](http://forums.boxee.tv/showthread.php?t=13206)
should help somewhat.
dh_make will set up a basic build system, that can easily be made usable (instead of taking the hours/days to set it up yourself).
You'll need to set up a GPG key to sign the .dsc, too.

---

### Post by Kissell on 2012-02-14
you guys ever get this to work?

There is no v1.50 released for 64-bit...  so I'd like to create it from the latest version source.

---

