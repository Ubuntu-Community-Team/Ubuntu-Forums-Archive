---
title: "jsapi.h where is it?"
date: 2005-12-05
forum: Programming Talk
---

### Post by Michael Matthews on 2005-12-05
** never mind ***  needed spidermonkey


I am trying to build gxine 0.5.1 but configure brings this error:

checking for smjs/jsapi.h... no
checking for js/jsapi.h... no
checking for /jsapi.h... no
checking for mozilla/js/jsapi.h... no
configure: error: libjs not found

/usr/lib/libjs.so exists, but I cannot find jsapi.h which is the actual problem.

I have installed
libjs0 - The NGS JavaScript interpreter - shared library
libjs0-dev - The NGS JavaScript interpreter - development files
libjscore-dev - javascript interpreter for OSB (development)
libjscore0 - javascript interpreter for OSB (runtime)

no luv.

---

### Post by SadaraX on 2006-12-27
If you have the firefox-dev package install, it has a copy of jsapi.h in its contents.

/usr/include/firefox/js/jsapi.h

---

