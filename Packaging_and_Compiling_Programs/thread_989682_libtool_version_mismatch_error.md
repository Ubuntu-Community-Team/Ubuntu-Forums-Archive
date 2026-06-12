---
title: "libtool version mismatch error"
date: 2008-11-21
forum: Packaging and Compiling Programs
---

### Post by phirestalker on 2008-11-21
I am trying to compile a program called oreka ([http://oreka.sourceforge.com/](http://oreka.sourceforge.com/)) but I am running into trouble.

```
libtool: Version mismatch error.  This is libtool 2.2.4 Debian-2.2.4-0ubuntu4, but the
libtool: definition of this LT_INIT comes from an older release.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.4 Debian-2.2.4-0ubuntu4
libtool: and run autoconf again.
```

I have tried to run aclocal to recreate aclocal.m4. the distribution of this source code seems to require a libtoolize --force command to link to the ltmain.sh as it is missing. I have tried autoconf and all kinds of things, I just don't know what to do. Please help

---

