---
title: "Install compiz extra plugins offline"
date: 2015-09-11
forum: New to Ubuntu
---

### Post by Muhammad_Al-Kady on 2015-09-11
I want to install compiz extra plugins offline because I have this error no mater what I did
```
fatal: unable to connect to anongit.compiz.org:
anongit.compiz.org[0: 94.247.179.16]: errno=Connection refused
```
Is there is ant way to install extra plugins offline??
Thanks.

---

### Post by Frogs Hair on 2015-09-11
Hello and Welcome 

Package dependencies are downloaded from the repositories in many cases and unless you have off-line source for those packages it is difficult to install applications. There is information and some instructions for offline repositories , but I have no experience setting up such a repository or using it.

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by deadflowr on 2015-09-11
You can download packages for offline installation by using
```
apt-get download <package-name-here>
```
This will download the package you want.
(FWIW, Ubuntu 14.04 or newer calls the compiz-plugins-extras package simply compiz-plugins; Ubuntu 12.04 calls the package compiz-plugins-extras)
It'll be in whatever directory you are in when you run the command. By default that directory would be the top level of your home directory.

You can then use dpkg to install, like so
```
sudo dpkg -i package-name.deb
```
replace package-name.deb witht the packages name; it'll end with a deb extension, though, so keep that.

As pointed out, you would also need to ensure you have all dependencies before trying to install the package.

On another note though,
You seem to be trying to download the plugins from the compiz git repository.
Why not try the versions in the Ubuntu repository which you would already have clean access to.
Most, if not all, of the extras plugins have been (seemingly)abandoned for years, and the Ubuntu devs who package it for Ubuntu probably put more work into getting what does exist work right within Ubuntu.

Hope it helps.

---

