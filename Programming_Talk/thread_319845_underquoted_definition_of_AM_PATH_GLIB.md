---
title: "underquoted definition of AM_PATH_GLIB ??????"
date: 2006-12-16
forum: Programming Talk
---

### Post by albesan on 2006-12-16
hello team,

Trying install from source and following installation instruction I get this:

./bootstrap
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB

could anybody tell me what this means? Thanks

a.

---

### Post by memoryhole on 2007-07-31
As irritating as it may be, and as useless an answer as this may be, the answer is either: "nothing" or "fix it yourself".

It's essentially a harmless error (it has (unlikely) potential for nastiness if you're *using* AM_PATH_GLIB), caused by the autoconf guys tightening up their restrictions on quoting and the glib guys being a bit cavalier about it. Most people can ignore the warning. If it really bugs you, or if that function is misbehaving and you need it to work, you can edit /usr/share/autoconf/glib-2.0.m4 and fix the quoting by hand... or just wait for the next version of glib to come out that will fix the problem.... or just downgrade your autoconf to a version that wasn't so picky.

---

### Post by perixx on 2007-12-17
Hi there, late response.... 

might pretty well be related to my problem here:
[http://ubuntuforums.org/showthread.php?p=3971336#post3971336]("http://ubuntuforums.org/showthread.php?p=3971336#post3971336")

perixx

---

