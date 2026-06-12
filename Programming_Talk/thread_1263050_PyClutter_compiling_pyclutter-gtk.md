---
title: "PyClutter: compiling pyclutter-gtk"
date: 2009-09-10
forum: Programming Talk
---

### Post by tom66 on 2009-09-10
I'm trying to compile pyclutter-gtk. Does anyone know if there are any easy .deb's or .rpm's I can use?

Anyway, if that option is unavailable, I'm compiling pyclutter-gtk. However, when it gets to the end of ./configure, it announces it's decided to not compile pyclutter-gtk:

```

...
config.status: creating Makefile
config.status: creating pyclutter.pc
config.status: creating docs/Makefile
config.status: creating docs/reference/entities.docbook
config.status: creating examples/Makefile
config.status: creating clutter/Makefile
config.status: creating clutter-gst/Makefile
config.status: creating clutter-gtk/Makefile
config.status: creating clutter-cairo/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
* PyClutter:
        build cluttergst:     no
        build cluttergtk:     no
        build cluttercairo:   no
        enable documentation: no

```

I've tried --with-pycluttergtk=yes and it still doesn't work. 

Any help appreciated.

---

