---
title: "help installing driver"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by dtrapp on 2014-03-22
I need some help installing a downloaded driver for an Epson printer on Ubuntu 13.10
The driver is an *.rpm file located in my ./opt directory and this was given as the command to install it
*# rpm -i epson-inkjet-printer-20121lw-1.0.0-1lsb3.2.i486.rpm*

Does this command look correct?
Do I need to move the file to another directory before installing?

Thanks for the help.

---

### Post by deadflowr on 2014-03-22
Since it's an rpm, perhaps try using alien
[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by buzzingrobot on 2014-03-22
An RPM is a package intended for use in Fedora/Red Hat/OpenSuse and other distributions.

Ubuntu uses the deb package format.  RPM's do not work on deb systems.  Alien, as mentioned, is a program that attempts to convert an rpm to a deb, or vice versa.  There is no certainty the converted package will install properly,

Before attempting alien, look around for a driver packaged in a deb for Ubuntu.

---

### Post by dtrapp on 2014-03-23
Hey guys-
I was able to find a *.deb package and installed it and it worked.
I am living the fat and happy life.
Thanks for the help

---

