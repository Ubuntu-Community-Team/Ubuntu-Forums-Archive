---
title: "Need help with autotools"
date: 2009-11-23
forum: Programming Talk
---

### Post by gastly on 2009-11-23
Hi guys, I'm trying to fiddle with Xchat by adding some custom stuff like custom notifications and stuff, just something to pass time that's all :P
By default, Xchat loads the libnotify libraries at runtime, but I thought it would be better to make it link with libnotify when compiling.

The problem is I can't seem to figure out how to add an option to get xchat to link with libnotify. Xchat uses autotools and I'm zero with autotools.

So, can anyone help me out here? :)

---

### Post by gastly on 2009-11-24
Well, I got it solved all by meself :P
I just added this code to **configure.in**, that's all:

```

AC_PATH_PROG(pkgconfigpath, pkg-config)
AC_MSG_CHECKING(for libnotify through pkg-config)
if $pkgconfigpath libnotify --exists; then
	CPPFLAGS="$CPPFLAGS `$pkgconfigpath --cflags libnotify`"
	LIBS="$LBS `$pkgconfigpath --libs libnotify`"
	AC_MSG_RESULT(yes)
fi

```

---

