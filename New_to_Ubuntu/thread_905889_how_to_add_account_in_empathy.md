---
title: "how to add account in empathy"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-30
i have installed empathy messenger its asking for some backend of every protocol now how to do that please help

---

### Post by mevets on 2008-08-30
I installed these packages to enable a lot of the backends:
```

sudo apt-get install libtelepathy-glib0 libtelepathy2 python-telepathy telepathy-butterfly telepathy-core telepathy-gabble telepathy-gnome telepathy-haze telepathy-idle telepathy-mission-control telepathy-salut telepathy-sofiasip telepathy-stream-engine libmissioncontrol-client0 libmissioncontrol-server1 telepathy-mission-control transmission empathy empathy-megaphone-applet libempathy-common

```
make sure you have
```

deb http://ppa.launchpad.net/telepathy/ubuntu hardy main

```
added to your /etc/apt/sources.list

---

### Post by imgkg on 2008-08-30
thanks it worked but i am not able to sign in into any account

---

