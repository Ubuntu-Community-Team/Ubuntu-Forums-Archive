---
title: "installation and configuration xwindow after installing ubuntu 16.4 (mini.iso)"
date: 2016-09-03
forum: New to Ubuntu
---

### Post by uu-uu on 2016-09-03
Prompt - how to install xwindow after minimal installation mini.iso (network boot)
which packages and configuration needed to start - work xserver

---

### Post by TheFu on 2016-09-03
Welcome to the forums.

It depends on how much X/Windows you want.  I don't have a list of things, but dependencies are pretty well covered, so if you install a program you want, that should pull in the dependencies of the dependencies of the dependencies and so on.  Realize that X/Client dependencies aren't the same as X/Server dependencies. This is so that we can load client programs which don't force an X-server to be loaded on server systems (which often don't have any GPU).

Anyone heading down this path isn't a beginner.

---

### Post by uu-uu on 2016-09-03
OK.
apt-get install xorg xserver-xorg
then xinit.
xterm can be run only by root.
what is missing?

---

