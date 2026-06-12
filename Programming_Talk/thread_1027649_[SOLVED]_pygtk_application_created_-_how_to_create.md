---
title: "[SOLVED] pygtk application created - how to create standard archive now?"
date: 2009-01-01
forum: Programming Talk
---

### Post by giuspen on 2009-01-01
I just finished my first application in pygtk.
I found information about the creation of a deb package from python source files [here]("http://showmedo.com/videos/video?name=linuxJensMakingDeb") but I can't find information about creating a standard ".tar.gz" source code archive, the classic archive from what, after extraction, we do configure->make->sudo checkinstall to create our ".deb" packages.
If anybody knows some useful links please help me.
Thanks.

---

### Post by ggaaron on 2009-01-07
Is there is any magic with this archive? If not:
tar -czf package.tar.gz list of files to put into archive

---

### Post by giuspen on 2009-01-08
> **ggaaron said:**
> Is there is any magic with this archive? If not:
tar -czf package.tar.gz list of files to put into archive

my problem is exactely that I don't' know what exactely files I have to put into the archive to let then people be able to install with the well known 

./configure
make
sudo install

(where, substituting sudo install with sudo checkinstall you create a package)

---

### Post by ggaaron on 2009-01-08
All the sources, data files(like images) if you need them and a Makefile with install target. You don't have to use autoconf/automake and ./configure with python and you don't have to compile it (though you can compile it to pyo/pyc if you like). For a really basic setup you need a Makefile that with install target will copy needed files to right directories.

---

