---
title: "HOWTO: Build gaim2 with bonjour/avahi support"
date: 2006-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by fago on 2006-10-29
Unfortunately edgy ships with a bonjour disabled gaim2 beta. So one has to compile gaim on his own:

just do
```

apt-get source gaim
apt-get build-dep gaim
apt-get install libavahi-compat-howl-dev
cd gaim-2.0.0+beta3.1
dpkg-buildpackage (as root)
dpkg -i gaim_2.0.0+beta3.1-1ubuntu9_i386.deb
gaim-data_2.0.0+beta3.1-1ubuntu9_all.deb

```

Then your gaim has bonjour support... :) To use it you have to add a new bonjour account.

---

### Post by stalefries on 2006-10-29
How do the bonjour accounts work?

---

### Post by fago on 2006-11-01
you create an account and set your nickname. that's it.

---

