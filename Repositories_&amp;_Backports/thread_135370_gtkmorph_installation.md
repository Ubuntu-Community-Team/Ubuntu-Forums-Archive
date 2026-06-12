---
title: "gtkmorph installation"
date: 2006-02-23
forum: Repositories &amp; Backports
---

### Post by spiregrain on 2006-02-23
I've installed gtkmorph in the usual way.  Synaptic reported that it needs libwaili too, so it went ahead and installed it.  But gtkmorph doesn't work.  This happens:
```
ken@franklin lib $ gtkmorph
gtkmorph: error while loading shared libraries: libwaili.so.1: cannot open shared object file: No such file or directory

```

Some other info:
```
ken@franklin lib $ locate libwai
/var/lib/dpkg/info/libwaili1.md5sums
/var/lib/dpkg/info/libwaili1.list
/var/lib/dpkg/info/libwaili-dev.postinst
/var/lib/dpkg/info/libwaili-dev.list
/var/lib/dpkg/info/libwaili-dev.prerm
/var/lib/dpkg/info/libwaili-dev.md5sums
/var/cache/apt/archives/libwaili1_19990723-15ubuntu2_i386.deb
/var/cache/apt/archives/libwaili-dev_19990723-15ubuntu2_i386.deb
/usr/share/doc/libwaili1
/usr/share/doc/libwaili1/changelog.Debian.gz
/usr/share/doc/libwaili1/copyright
/usr/share/doc/libwaili-dev
/usr/share/doc/libwaili-dev/changelog.Debian.gz
/usr/share/doc/libwaili-dev/README.Debian
/usr/share/doc/libwaili-dev/copyright
/usr/share/doc/libwailic2
/usr/lib/libwaili.a
/usr/lib/libwaili.la

```

```
ken@franklin lib $ ls -l libwail*
-rw-r--r--  1 root root 853042 2005-09-04 04:42 libwaili.a
-rw-r--r--  1 root root    849 2005-09-04 04:42 libwaili.la
lrwxrwxrwx  1 root root     17 2006-02-21 19:14 libwaili.so -> libwaili.so.1.0.0

```

```
ken@franklin lib $ ls libwaili.so.1*
ls: libwaili.so.1*: No such file or directory

```

Any thoughts?  Any suggested alternatives to gtkmorph?

---

### Post by Jingo on 2006-03-20
Same problem!

---

### Post by Stone123 on 2006-04-25
It works in dapper. does anyone have some tutorial on gtkmorph , xmorph is maby other solution but it looks old.

---

