---
title: "aclocal warning"
date: 2007-01-20
forum: Programming Talk
---

### Post by kiplingw on 2007-01-20
Whenever aclocal is executed, I see the following printed to stdout:

$ aclocal
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/libart.m4:11: warning: underquoted definition of AM_PATH_LIBART
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE


I am not sure what the warnings / errors mean or how to go about addressing them.

Kip

---

### Post by hod139 on 2007-01-22
They look to be just warnings, so I wouldn't worry too much.  Sorry I'm not more helpful.

---

### Post by kiplingw on 2007-01-23
That they are, but I would still like to get rid of them.

Kip

---

