---
title: "Downloading Qt"
date: 2008-09-04
forum: Programming Talk
---

### Post by japtar10101 on 2008-09-04
My class team project will be developing a game using Qt graphic library in C++.  There are so many packages on synaptics, I wasn't sure which one to download.  Which package am I supposed to install to get it's library?

It's also worth noting that when I try to download libglib2.0-dev (a dependency of libqt4-dev), it gives me this error:
```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-dev_2.16.4-0ubuntu2_i386.deb
  404 Not Found [IP: 91.189.88.31 80]
```
I guess package libglib2.0 doesn't exist for any reason?:confused:

Finally, the version I'm looking for is the most updated, v4.4.*

---

### Post by damis648 on 2008-09-04
I would know exactly, but see what dependecies are given when installing any qt app (just try installing k3b, for example).

---

### Post by japtar10101 on 2008-09-04
I forgot to mark this as a ubuntu question, but sure, I'll test that out.

Edit: Oh, you can't mark distributions in this board...

---

### Post by japtar10101 on 2008-09-04
K3b installed fine.  Not sure if it's safe to run KDE stuff in a GNOME environment, but the libglib-dev package was not a part of it's dependency.

Actually, what is libqt4-dev package?  Is that for developing qt library, or qt C++ application program?

---

### Post by sonofusion82 on 2008-09-04
yes, libqt4-dev is what you need to start developing apps in Qt4.
the packages in hardy repo is probably still using Qt4.3 which should be fine for most Qt4 development.
If you really need the latest Qt4.4, you will probably need to download it from Trolltech or KDE4's qt-copy and build from source.

---

### Post by Zugzwang on 2008-09-05
> **sonofusion82 said:**
> 
If you really need the latest Qt4.4, you will probably need to download it from Trolltech or KDE4's qt-copy and build from source.

A not so good advice. Don't do so if not absolutely necessary.

Try setting your "package source" to a different server. That one might have problems.

---

### Post by samjh on 2008-09-05
> **sonofusion82 said:**
> yes, libqt4-dev is what you need to start developing apps in Qt4.
the packages in hardy repo is probably still using Qt4.3 which should be fine for most Qt4 development.
If you really need the latest Qt4.4, you will probably need to download it from Trolltech or KDE4's qt-copy and build from source.

Hardy has Qt4.4.

I don't have Ubuntu installed right now (got Fedora 9 instead), but from memory you should download:
[list][*]libqt4-dev[*]qt4-devtools[*]qt4-doc[/list]The package names are probably a little off, as I'm going purely from memory here.  Just look for things reasonably similar in Synaptic.

---

### Post by sonofusion82 on 2008-09-15
> **samjh said:**
> Hardy has Qt4.4.


nope, it is in only hardy-backports and since i don't really use backports, i m using Qt4.3
[http://packages.ubuntu.com/hardy-backports/qt4-dev-tools](http://packages.ubuntu.com/hardy-backports/qt4-dev-tools)
[http://packages.ubuntu.com/hardy/qt4-dev-tools](http://packages.ubuntu.com/hardy/qt4-dev-tools)

---

