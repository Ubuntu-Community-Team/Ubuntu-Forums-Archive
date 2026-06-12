---
title: "Problems in running autoconf under ubuntu"
date: 2007-08-16
forum: Programming Talk
---

### Post by yinglcs2 on 2007-08-16
Hi,

I am trying to run autoconf under ubuntu.

I am getting the following error:  
Can you please tell me where are those macros are defined? How can i fix my problem?

Thank you.


Copying file po/Makevars.template
+ rm -f po/Makevars.template
+ aclocal-1.9 -I /root/build-bin/share/aclocal-1.9 -I
/root/build-bin/share/aclocal -I /root/build-bin/share/autoconf -I
/root/video-dep-bin/share/aclocal -I m4
+ autoconf
configure.ac:1: error: possibly undefined macro: dnl
     If this token and others are legitimate, please use m4_pattern_allow.
     See the Autoconf documentation.
configure.ac:27: error: possibly undefined macro: AS_IF
configure.ac:41: error: possibly undefined macro: AC_DEFINE
configure.ac:78: error: possibly undefined macro: AC_MSG_ERROR
configure.ac:81: error: possibly undefined macro: AC_MSG_WARN
configure.ac:181: error: possibly undefined macro: AC_ARG_ENABLE
configure.ac:379: error: possibly undefined macro: AC_CHECK_LIB
configure.ac:449: error: possibly undefined macro: AC_CHECK_HEADERS
configure.ac:2089: error: possibly undefined macro: AC_PATH_PROG
configure.ac:5094: error: possibly undefined macro: AC_PATH_PROGS

---

