---
title: "Super Star Trek missing ncursesw [NOT BSD GAMES]"
date: 2009-10-27
forum: Programming Talk
---

### Post by Augustus Maxim on 2009-10-27
I was browsing [ESR's site]("http://catb.org/%7Eesr") and came across a game called [Super Star Trek]("http://sst.berlios.de/") (trek with some different features than BSD trek) that looked fun and the code is not terribly hard to understand. So, wanting to play it. I downloaded it and ran the configure script. But I got an error:

```

checking for newwin in -lncursesw... no
configure: error: ncurses library is missing on your system.

```So I installed libncurses5-dev and ran configure again. I got the same error! I then ran

```
locate ncursesw
```Which returned

```

/lib/libncursesw.so.5
/lib/libncursesw.so.5.6
/usr/bin/ncursesw5-config
/usr/share/doc/libncursesw5
/usr/share/doc/libncursesw5/changelog.Debian.gz
/usr/share/doc/libncursesw5/copyright
/var/lib/dpkg/info/libncursesw5.list
/var/lib/dpkg/info/libncursesw5.postinst
/var/lib/dpkg/info/libncursesw5.postrm
/var/lib/dpkg/info/libncursesw5.shlibs

```I tried changing the ncursesw parameter in the configure.ac file and running autoconf, but still to no avail.

I am pretty much at my wits end with this and would like to know if anyone knows how to solve my problem.

Thank you,
Augustus


####SOLUTION########
Simply install libncursesw5-dev_5.6. I feel slightly stupid now :)

---

