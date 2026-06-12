---
title: "bamfdaemon"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-04-26
Running 12.04.  I have an icon in my unity launcher, gery with a question mark in the middle of it and a little arrow to the left - which I bellieve indicates it is running.  When I hover the mouse of it, it says bamfdaemon.  Had a look in system monitor and there is a bamfdaemon process running /usr/lib/bamf/bamfdaemon.  I've just reinstalled 12.04 from stratch - never had this before.  Any help appreciated telling what this is and how to stop it.

---

### Post by mcduck on 2014-04-26
running *apt-cache show bamfdaemon* gives the following description:

> Window matching library - daemon bamf matches application windows to desktop files
This package contains the daemon used by the library and a gio module that facilitates the matching of applications started through GDesktopAppInfo

I doubt you'd like to stop the service itself, it's more a question of what's wrong with that particular launcher icon that's causing bamfdaemon to fail trying to match it correctly to a running application...

I'm not sure if it logs errors somewhere, but taking a look at ~/.xsession-errors might be a good start.

---

