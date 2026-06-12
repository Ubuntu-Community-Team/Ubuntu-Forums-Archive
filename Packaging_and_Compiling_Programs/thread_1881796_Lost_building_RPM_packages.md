---
title: "Lost building RPM packages"
date: 2011-11-16
forum: Packaging and Compiling Programs
---

### Post by Karamba75 on 2011-11-16
Hi Everyone,

I'm not a Ubuntu expert but I had a script that was building Debian and RPM packages just fine in Ubuntu 606. Now that I have to do it on 1104, I constantly get this error :

cannot stat `/usr/lib/rpm/RPMS/i386/*.rpm'

I tried different paths (the original one was '/usr/src/rpm') with no success. So I was wondering which path should I use or if I've missed installing something ? I'm stuck...

Thanks for your help.

Karamba

---

### Post by BillyBoa on 2011-11-16
You could convert the .rpm to .deb

[http://www.thegeekstuff.com/2010/11/alien-command-examples/](http://www.thegeekstuff.com/2010/11/alien-command-examples/)

installing the package Alien

---

### Post by Karamba75 on 2011-11-16
Doesn't work for me. Alien fails complaining about being unable to stat to a directory I don't know about.

---

