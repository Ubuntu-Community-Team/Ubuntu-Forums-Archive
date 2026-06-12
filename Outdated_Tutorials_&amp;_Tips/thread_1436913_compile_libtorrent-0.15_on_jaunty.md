---
title: "compile libtorrent-0.15 on jaunty"
date: 2010-03-23
forum: Outdated Tutorials &amp; Tips
---

### Post by binary.koala on 2010-03-23
on jaunty, gcc 4.3.3. python 2.6 there is a slight problem with configuring libtorrent-0.15 ([http://www.rasterbar.com/products/libtorrent/building.html](http://www.rasterbar.com/products/libtorrent/building.html)) when required to compile with python bindings.
command:
```
./configure --enable-python-binding
```
yields:
```
configure: error: Boost.Python library not found. Try using --with-boost-python=lib.
```
which happens regardless if libboost1.37-dev is installed.
the problem is that libboost in ubuntu comes in its -mt (multithread) version, which is reflected in the filename of the lib:
```
/usr/lib/libboost_python-mt.so
```
configure script in libtorrent-0.15 (more exactly m4 script) can't find the right version and exit. all needed is to add postfix 'mt' to the ./configure script:
```
./configure --enable-python-binding --with-boost-python=mt
```
after that ./configure finishes with no error.

---

