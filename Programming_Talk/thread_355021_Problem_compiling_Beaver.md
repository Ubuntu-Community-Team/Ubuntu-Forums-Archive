---
title: "Problem compiling Beaver"
date: 2007-02-06
forum: Programming Talk
---

### Post by Paxet on 2007-02-06
The project web page is --> [http://www.nongnu.org/beaver/]("http://www.nongnu.org/beaver/")

When trying to compile it under Ubuntu 6.06 with automake 1.9 I'm getting the following errors: 

Copying file po/Rules-quot
Copying file po/boldquot.sed
Copying file po/en@boldquot.header
Copying file po/en@quot.header
Copying file po/insert-header.sin
Copying file po/quot.sed
Copying file po/remove-potcdate.sin
Putting files in AC_CONFIG_AUX_DIR, `config'.
configure.ac:114: error: possibly undefined macro: PKG_CFLAGS
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:115: error: possibly undefined macro: PKG_LIBS
configure:25337: error: possibly undefined macro: PKG_PKG_ERRORS
autoreconf: /usr/bin/autoconf failed with exit status: 1

Do you know how to solve this?
Thanks :)

---

