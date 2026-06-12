---
title: "will digikam run in Xubuntu 12.04?"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by aspergerian on 2013-02-17
Will digikam run in Xubuntu 12.04?

---

### Post by aspergerian on 2013-02-18
> **aspergerian said:**
> Will digikam run in Xubuntu 12.04?

I found this
sudo apt-get --no-install-recommends install digikam
at
[http://ubuntu.igameilive.com/2011/08/installing-digikam-in-ubuntu-without.html](http://ubuntu.igameilive.com/2011/08/installing-digikam-in-ubuntu-without.html)

Is the terminal command valid?

I'm being cautious, that's why I'm not just rushing forth.

---

### Post by PhilGil on 2013-02-18
> **aspergerian said:**
> Is the terminal command valid?

I'm being cautious, that's why I'm not just rushing forth.
Yes, that will give you a working install of DigiKam, but it's possible some extras won't work.

A software center install of a package will include the package's hard dependencies as well as packages that are recommended for the install. The "no-install-recommends" option tells the package manager to only install the hard dependencies. The program will work without the recommended packages, but some ancillary functionality may fail.

DigiKam is a KDE program, so not installing the recommends does make the install considerably smaller, as fewer KDE packages will be included.

---

### Post by ibjsb4 on 2013-02-18
I just tried both ways.

With recommends = 360M

Without recommends = 260M

IMO, either way you get dumped on with KDE dependences.

[http://packages.ubuntu.com/precise/digikam](http://packages.ubuntu.com/precise/digikam)

---

### Post by aspergerian on 2013-02-19
PhilGil & ibjsb4,

Thank you for the replies. I'm far from understanding how KDE packages run within Xubuntu 12.04.1. My primary concern is that I don't want to break my Xubu installation. Also, I haven't found a chart that delineates what functions the "extras" provide.

[http://www.digikam.org/](http://www.digikam.org/)

---

