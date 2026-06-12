---
title: "Debian Packaging"
date: 2007-05-15
forum: Programming Talk
---

### Post by Zaff on 2007-05-15
Hi I know this is just a little off topic but i'm having problems building a debian source package.
Basically I have a debian package that compiles en python library. So far so good.
Now I'm trying to build the source using the following command :  dpkg-source -b <name of package>.
I get the regular tar.gz file and the dsc file but this dsc file doesn't look like it should. here's what I get :
Format: 1.0
Source: package
Binary: package
Architecture: any
Version: 2.1.0-3
Maintainer: Thomas
Standards-Version: 3.6.0
Build-Depends: debhelper (>= 5.0.38), libvpl-dev (>= 1.0.3-2), python-all-dev (>= 2.3.5-11), python-central (>= 0.5.6)
Files: 
 bc4c0b817f37e9dba13b25aa64bfb058 325038 cvapi_2.1.0-3.tar.gz
Python-Version: all

Now if i upload it as such it fails. The system administrator told me that the dsc file shouldn't finish with the Python-Version line but with the Files line. Apparently they are inverted.
Anyway, has anyone ever had that problem and if so how can it be corrected ?
Thanks for answering as soon as possible.
Tom

---

