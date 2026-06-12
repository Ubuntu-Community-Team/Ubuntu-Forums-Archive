---
title: "GNU gettext tools not found; required for intltool"
date: 2009-02-25
forum: Packaging and Compiling Programs
---

### Post by StarF on 2009-02-25
trying to do a install of RRD Tool from this guide:

[http://technotim.dyndns.org/index.php?option=com_content&task=view&id=80&Itemid=13](http://technotim.dyndns.org/index.php?option=com_content&task=view&id=80&Itemid=13)

when i run the .config i am getting this error:

> Libintl Processing
checking for locale.h... (cached) yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... no
checking for intltool >= 0.35.0... 0.37.1 found
checking for xgettext... no
checking for msgmerge... no
checking for msgfmt... (cached) no
configure: error: GNU gettext tools not found; required for intltool

how do i fix this?

---

### Post by geirha on 2009-02-26
Install gettext. ```
sudo aptitude install gettext
```

---

### Post by Mak_PG on 2009-03-10
Thanxs!:D

---

### Post by marcurius on 2009-08-20
Thanks!

---

### Post by xavico on 2010-03-12
its works but.. i have another throuble > 

checking for PACKAGE... configure: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
 :(

---

### Post by SevenMachines on 2010-03-13
as the error mentions, you probably dont have pkg-config installed

$sudo apt-get install pkg-config

---

