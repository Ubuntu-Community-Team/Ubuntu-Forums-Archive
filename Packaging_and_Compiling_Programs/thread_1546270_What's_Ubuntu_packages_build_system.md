---
title: "What's Ubuntu packages build system?"
date: 2010-08-05
forum: Packaging and Compiling Programs
---

### Post by holmes86 on 2010-08-05
hi,all

I want to know about ubuntu packages build system.for example,Fedora build system is koji,opensuse build system is obs. Is there any build system as koji or obs for ubuntu&#65311;

thanks very much

---

### Post by interval1066 on 2010-08-06
Ubuntu uses the Debian package format and an app called dpkg to make them, but its kind of a dark art, not a nice bundle like koji. You need to install dpkg-dev, fakeroot, and the usual programming utils. You can find out more at [this place](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/), but you might sniff around for something more up-to-date. At least using them is easy with Synaptics.

---

