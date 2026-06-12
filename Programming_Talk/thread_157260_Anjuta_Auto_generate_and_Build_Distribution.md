---
title: "Anjuta: Auto generate and Build Distribution"
date: 2006-04-08
forum: Programming Talk
---

### Post by Daniel Ngu on 2006-04-08
Hi,

I'm kept getting these two red lines of text from _Build->Auto generate_:

[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `po' not in SUBDIRS[/COLOR]
[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `intl' not in SUBDIRS[/COLOR]

However, _Build->Build All_ completed successfully.

_Build->Execute_ ran successfully as well.

However, _Build->Build Distribution_ gives the following:

[COLOR="RoyalBlue"]configure.in: 78: required file `./ABOUT-NLS' not found[/COLOR]
[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `po' not in SUBDIRS[/COLOR]
[COLOR="Red"]Makefile.am:6: AM_GNU_GETTEXT in `configure.in' but `intl' not in SUBDIRS[/COLOR]
[COLOR="RoyalBlue"]automake: Makefile.am: AM_GNU_GETTEXT in `configure.in' but `ALL_LINGUAS' not defined[/COLOR]
[COLOR="RoyalBlue"]make: *** [distdir] Error 1[/COLOR]
Completed ... unsuccessful

Am I missing any packages that might be causing this?

Thanks in advance.

Daniel

---

### Post by cro.smiley on 2006-04-09
You can try Build > Configure.
It should say if you need some packages.

---

### Post by Rob_Frohne on 2006-12-17
Hi,

I  am wondering if you solved this.  I have the same problem, if I disable GETTEXT when I set up the project.  If I enable GETTEXT when I set up the project, I get rid of the po problem, but the intl one still  is there.

Thanks,

Rob

---

