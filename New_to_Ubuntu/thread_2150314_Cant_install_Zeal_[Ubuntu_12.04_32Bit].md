---
title: "Cant install Zeal [Ubuntu 12.04 32Bit]"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by violetkiwi on 2013-05-31
[http://zealdocs.org/download.html](http://zealdocs.org/download.html)



The following packages have unmet dependencies:
 zeal : Depends: libqt5core5 (>= 5.0.1+dfsg) but it is not installable
        Depends: libqt5gui5 (>= 5.0.1+dfsg) but it is not installable
        Depends: libqt5network5 (>= 5.0.1+dfsg) but it is not installable
        Depends: libqt5sql5 (>= 5.0.1+dfsg) but it is not installable
        Depends: libqt5webkit5 but it is not installable
        Depends: libqt5widgets5 (>= 5.0.1+dfsg) but it is not installable
        Depends: libqt5xml5 (>= 5.0.1+dfsg) but it is not installable
        Depends: libqt5location5 but it is not installable
        Depends: libqt5quick5 but it is not installable
        Depends: libqt5qml5 but it is not installable
        Depends: libqt5sensors5 but it is not installable
        Depends: libqt5opengl5 but it is not installable
        Depends: libqt5sql5-sqlite but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by oldos2er on 2013-05-31
Did you add the Qt5 PPAs? [https://launchpad.net/~jerzy-kozera/+archive/zeal-ppa](https://launchpad.net/~jerzy-kozera/+archive/zeal-ppa)

---

### Post by violetkiwi on 2013-05-31
> **oldos2er said:**
> Did you add the Qt5 PPAs? [https://launchpad.net/~jerzy-kozera/+archive/zeal-ppa](https://launchpad.net/~jerzy-kozera/+archive/zeal-ppa)


i haved addedtwo urls into repository option in synaptic package manager .zeal is shown in synaptic list

---

### Post by oldos2er on 2013-05-31
After you add the PPAs you need to refresh your sources lists, in Synaptic click Reload.

---

### Post by violetkiwi on 2013-05-31
> **oldos2er said:**
> After you add the PPAs you need to refresh your sources lists, in Synaptic click Reload.

i have done it.
Synaptic shows zeal, but cant install ,it shows the error in first post

---

### Post by oldos2er on 2013-06-01
Have you tried clicking Edit, Fix Broken Packages?

---

