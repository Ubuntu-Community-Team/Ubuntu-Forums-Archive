---
title: "Anjuta warning"
date: 2005-06-23
forum: Programming Talk
---

### Post by oldmarti on 2005-06-23
Hi,
When I generate new project in anujta receive some warning. They are not fatal, and I  can compile and run program. Here is the warnings:

/usr/share/aclocal/pkg.m4:5: warning: underquoted definition of PKG_CHECK_MODULES
/usr/share/aclocal/aalib.m4:12:warning: underquoted definition of AM_PATH_AALIBautoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.

It's is possible to make somethink to remove this warning? I try automake1.4 and automake1.9 - no difference.

---

