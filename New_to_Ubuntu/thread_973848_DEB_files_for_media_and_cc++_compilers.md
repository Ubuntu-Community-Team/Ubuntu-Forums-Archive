---
title: "DEB files for media and c/c++ compilers"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Sushubh on 2008-11-07
i have to install ubuntu on a friend's machine which has no internet connectivity. 

i was hoping to get direct deb file links to installers of media codecs and compilers for c and c++...

---

### Post by renzokuken on 2008-11-07
all debs from the repos can be got from [packages.ubuntu.com](packages.ubuntu.com)

just search and download the ones you want, transfer them via usb or cd or whatever takes your fancy, then install them with

```
sudo dpkg -i *nameoffile*.deb
```

for compilers check the **build-essential** package and its dependencies (its actually a meta-package so refers to and installs a group of others. media codecs you might be able to get from the medibuntu repos

---

### Post by mapes12 on 2008-11-07
System>Administration> Synaptic Package Manger and search for aptoncd

The home page is here: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by Sushubh on 2008-11-07
cool thanks :D

---

