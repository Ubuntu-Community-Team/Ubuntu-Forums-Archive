---
title: "Installing Qt 5.1 for development on Ubuntu 13.04"
date: 2013-08-25
forum: New to Ubuntu
---

### Post by nixeagle on 2013-08-25
Question is in the title. Right now I see support for Qt 5.0, but not for 5.1. I would like to make use of some of the new Qt Quick improvements in a program I am writing.

---

### Post by tgalati4 on 2013-08-25
Is there a PPA for 5.1?  Some guidance:  [http://askubuntu.com/questions/279421/how-can-i-install-qt-5-x-on-12-04-lts](http://askubuntu.com/questions/279421/how-can-i-install-qt-5-x-on-12-04-lts)

---

### Post by nixeagle on 2013-09-02
Following those instructions I get told the PPA is obsolete.

---

### Post by GwL3eNC on 2013-09-02
Is this what you are looking for

[http://packages.ubuntu.com/raring/qtbase5-dev](http://packages.ubuntu.com/raring/qtbase5-dev)

If so, on the bottom of the packe you can download the debian file and
install it with

sudo dpkg -i packetname

or download a run file here [http://qt-project.org/downloads](http://qt-project.org/downloads)

or here [http://qt-project.org/wiki/Qt-5-unofficial-builds](http://qt-project.org/wiki/Qt-5-unofficial-builds), but this are suse rpm files.
[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux      ]("http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/")

---

