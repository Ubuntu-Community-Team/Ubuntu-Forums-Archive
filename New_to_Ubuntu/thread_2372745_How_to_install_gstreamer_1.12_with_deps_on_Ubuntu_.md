---
title: "How to install gstreamer 1.12 with deps on Ubuntu 16"
date: 2017-09-28
forum: New to Ubuntu
---

### Post by evgenios24 on 2017-09-28
Hi!

I need to install newest version on Gtreamer will all plugins on Ubuntu 16 (server).

I've just found them all on [https://launchpad.net/ubuntu/+source/gstreamer1.0/1.12.3-1/+build/13448769](https://launchpad.net/ubuntu/+source/gstreamer1.0/1.12.3-1/+build/13448769) but now I need to install too many packages and their deps separately. 

Is it possible to install all GS 1.12 from launchpad by simple command?

Thanks.

---

### Post by dirkjot on 2017-11-25
Gstreamer is usually not backported to older releases because too many packages depend on it.  Upgrading to Ubuntu 17.10 (Artful) is your easiest option.

---

