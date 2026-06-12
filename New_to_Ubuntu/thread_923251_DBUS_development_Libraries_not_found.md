---
title: "DBUS development Libraries not found"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by deepdhan on 2008-09-18
Hi,
 I have installed DBUS, and while trying to configure glib, i get checking pkg-config is at least version 0.9.0... yes
checking for DBUS... no
configure: error: DBus development libraries not found

i have also done export PKG_CONFIG_PATH to appropriate path.


please help!!!!

---

### Post by MegaJim on 2008-09-18
you've installed the dev packages? dbus-*-dev?

---

### Post by deepdhan on 2008-09-18
Yes i have installed both the dev files
libdbus-glib-1-dev
libdbus-1-dev

still no luck :(

---

### Post by sextheorist on 2010-11-24
thanks....

installing dbus-*dev from synaptic package manager solved the problem.


If you are having problems while using ./configure then it is necessary to install packages ending with -dev . no other package will work.:P

---

