---
title: "making debs from svn"
date: 2007-08-10
forum: Programming Talk
---

### Post by dbbolton on 2007-08-10
first off, i'm not sure if this is the right forum. however, since it would appear that i'll have to edit some c files, it seems remotely appropriate.

so, i'm trying to build a deb for visibility (i did this for ttm and it worked out fine). here is the trac page for visibility: [http://projects.l3ib.org/trac/visibility](http://projects.l3ib.org/trac/visibility)

i checked out from the svn, ran ./bootstrap, ./configure, and make. when i ran checkinstall -D, it said that the package version was 'svn' and dpkg doesn't like that since the version doesn't contain any digits. so, i opened up the Makefile, and changed this:
```

PACKAGE_STRING = visibility svn
PACKAGE_VERSION = svn
VERSION = svn

```

to this:
```

PACKAGE_STRING = visibility 0.0
PACKAGE_VERSION = 0.0
VERSION = 0.0

```

however, checkinstall is still saying that the upstream version is 'svn'. so basically, i want to know what i need to change in order to give dpkg a version for this package.

thanks in advance :)

---

