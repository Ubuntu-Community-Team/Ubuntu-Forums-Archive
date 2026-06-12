---
title: "packaging NetworkManager"
date: 2007-04-27
forum: Packaging and Compiling Programs
---

### Post by duff on 2007-04-27
Hi --

Has anybody been able to create the suite of debs needed for Network Manger.  I've been able to build and install NetworkManager 0.6.5 + nm-applet 0.6.5 into my /opt directory and it works (0.6.4 won't connect to my campus's wireless network).  Now, I'd like to really get it into my system (properly), so it'll just come up by itself.  The problem is there's no "debian" directory to easily create the debs, and checkinstall wants to create one entire package, instead of the way it's set up in fiesty with libnm-glib, libnm-util, network-manager, network-manager-gnome, etc.  And libnm-glib has quite a few dependencies.  Any ideas?

Thanks.

---

