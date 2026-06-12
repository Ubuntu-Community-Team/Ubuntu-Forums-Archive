---
title: "Dependencies: Slib, guile &amp; gnome2"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by LearningPerson on 2008-09-11
Hello,

Have had problems since I had to do a manual fsck.  Tried to install Gnucash in Synaptic and Terminal and found that I was missing some stuff: Gnome2, slib & guile (although it's marked as installed in Synaptic?).   Something is also locked.  Here's what I see when trying to install slib from the Terminal:


Setting up slib (3a4-4) ...
Cannot open `/usr/share/doc-base/data/scrollkeeper.map' for reading: No such file or directory at /usr/share/perl5/Debian/DocBase/Programs/Scrollkeeper.pm line 60
dpkg: error processing slib (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of guile-1.6-slib:
 guile-1.6-slib depends on slib (>= 3a2-3); however:
  Package slib is not configured yet.
dpkg: error processing guile-1.6-slib (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 slib
 guile-1.6-slib

Am using Hardy Heron.

Thanks, 
Sharon

---

