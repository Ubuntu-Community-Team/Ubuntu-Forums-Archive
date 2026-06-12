---
title: "XU4 - Ultima4 CVS compiled (.deb)"
date: 2008-02-26
forum: Packaging and Compiling Programs
---

### Post by warbird on 2008-02-26
I've compiled the CVS version of XU4, and included the freeware U4 + updates in the .deb.

The deb is made with checkinstall. tested on my system, and everything works. No guaranties for anyone else though. 1 problem I have is when uninstalling:

dpkg - warning: while removing xu4, directory `/usr/local/bin' not empty so not removed.
dpkg - warning: while removing xu4, directory `/usr/local/games' not empty so not removed.
dpkg - warning: while removing xu4, directory `/usr/local/share/applications' not empty so not removed.
dpkg - warning: while removing xu4, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing xu4, directory `/usr/local' not empty so not removed.

How can I specify that these should not be removed, when creating the .deb? Can anyone help?

edit: too big to attach (1.9 mb), here is a rapidshare link for anyone interested:

[http://rapidshare.com/files/95175766/xu4_20080226-1_i386.deb.html](http://rapidshare.com/files/95175766/xu4_20080226-1_i386.deb.html)

---

### Post by joxenford on 2008-03-19
thanks warbird!  I can't wait to give this a shot.  I've been unable to speak with Hawkwind the seer and I'm hoping a recent build will help.

Thanks again!

---

