---
title: "Getting Glade apps to compile"
date: 2006-08-03
forum: Programming Talk
---

### Post by phorque on 2006-08-03
Hi. I'm trying to compile a really basic GTK app from a Glade design and when running the "autogen.sh" I get this message.

> 
checking for GTKMM... configure: error: Package requirements (gtkmm-2.0 >= 2.2.12) were not met:

No package 'gtkmm-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTKMM_CFLAGS
and GTKMM_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

This doesn't make much sense because I have both libgtkmm2.0-1c2a and libgtkmm-2.4-1c2a installed... but there is no gtkmm package on its own.

What are you supposed to do to get the damn things to compile?

---

### Post by Hanj on 2006-08-03
You need the development packages to compile programs. It's called libgtkmm-2.4-dev. The regular package is just for running programs.

---

