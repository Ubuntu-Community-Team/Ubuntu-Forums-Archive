---
title: "how do I get updates in trinity?"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by thane1 on 2013-02-15
Installed the latest Trinity stable desktop environment with Ubuntu Precise (complete all in one package) into vbox last night to try out (version 3.5.13.1).  All seems well so far, except that nowhere can I find a way to get security or other updates via the menu system.  I can always do this via terminal.  But there must be a way to do it via the gui.  Any suggestions?  thanks

---

### Post by Frogs Hair on 2013-02-15
Updates would come through the repository and the link includes sources for 12.04 but I would check software sources or the/etc/apt/sources to see it the repository was added during installation.  [http://www.trinitydesktop.org/wiki/bin/view/Documentation/UbuntuBinaryInstallation](http://www.trinitydesktop.org/wiki/bin/view/Documentation/UbuntuBinaryInstallation)

Some times stand alone .deb packages are as is and don't update.

---

### Post by thane1 on 2013-02-16
Thanks for the reply.  I added the debs from your link and did an apt-get update.  Seemed to work fine.  But after restarting I still seem to have no access in the gui to software sources or updating.  This Trinity version is kde-based and I've only somewhat used kde before.  I'm a little unfamiliar with what I should be looking for.

---

