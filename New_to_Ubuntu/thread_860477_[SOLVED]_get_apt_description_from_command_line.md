---
title: "[SOLVED] get apt description from command line"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by PGScooter on 2008-07-15
Hi, I would like to get the descriptions of packages from the command line but cannot find an option to do so. Is there one for apt-cache or apt-get? I just want the description without having to open up synaptic,

thanks

---

### Post by bobnutfield on 2008-07-15
Try:

> apt-cache show <package>

---

### Post by PGScooter on 2008-07-15
that did it, thanks!

---

### Post by phidia on 2008-07-15
I think dselect will provide package information and aptitude too. Take a look at the [debian FAQ]("http://www.debian.org/doc/FAQ/ch-pkgtools.en.html") on package management.

---

