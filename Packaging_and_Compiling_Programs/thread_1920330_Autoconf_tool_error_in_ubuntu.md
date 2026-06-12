---
title: "Autoconf tool error in ubuntu"
date: 2012-02-04
forum: Packaging and Compiling Programs
---

### Post by aaalbatrosss on 2012-02-04
When I try to build with linux-headers-3.2.0

configure.ac file:

```
dnl ---------------------------------------------
dnl freetype
dnl ---------------------------------------------
dnl Test for freetype
[COLOR="Red"]PKG_CHECK_MODULES([TTF], [freetype2])[/COLOR]

dnl ---------------------------------------------
dnl libxml2
dnl ---------------------------------------------
dnl Test for libxml2

AC_PATH_PROG(LIBXML2_CONFIG,xml2-config,no)
if test "$LIBXML2_CONFIG" = "no" ; then
AC_MSG_ERROR(libxml2 needed and xml2-config not found)
else
XML2_LIBS="`$LIBXML2_CONFIG --libs`"
XML2_FLAG="`$LIBXML2_CONFIG --cflags`"
AC_DEFINE(HAVE_LIBXML2,,[LIBXML2 support])  
fi
AC_SUBST(XML2_LIBS)
AC_SUBST(XML2_FLAG)
```

get this error:

```
./configure: line 7979: syntax error near unexpected token `TTF,'
./configure: line 7979: `PKG_CHECK_MODULES(TTF, freetype2)'
```

What is wrong?

pkg-config is instaled.

How do I include this.

Thanks

---

