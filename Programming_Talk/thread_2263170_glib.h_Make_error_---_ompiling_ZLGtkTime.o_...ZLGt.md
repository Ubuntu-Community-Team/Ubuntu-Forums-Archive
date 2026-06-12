---
title: "glib.h Make error --- ompiling ZLGtkTime.o ...ZLGtkTime.cpp:20:18: fatal error: glib."
date: 2015-01-30
forum: Programming Talk
---

### Post by harkirat_singh on 2015-01-30
Compiling fbreader open source
when i type make command it gives an error like [I]fatal error: glib.h: No such file or directory
[/I]i searched it on the internet then i came to the following solution.

> I added the output of  **pkg-config --cflags glib-2.0** to the root make file like this --> [COLOR=#000000]*GCC = -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include  -lglib-2.0*[/COLOR] but still the error occurs.
please tell me where i am lacking. ?

---

### Post by schragge on 2015-01-30
This will install [build-dependencies]("https://www.debian.org/doc/debian-policy/ch-relationships.html#s-sourcebinarydeps") of *fbreader*, among them *libgtk2.0-dev* and *libglib2.0-dev*:
```
sudo apt-get build-dep fbreader
```

---

### Post by harkirat_singh on 2015-01-31
Thank you.. i solved it :)

---

