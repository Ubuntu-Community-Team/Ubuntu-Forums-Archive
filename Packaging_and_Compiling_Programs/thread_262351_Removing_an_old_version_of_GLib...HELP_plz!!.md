---
title: "Removing an old version of GLib...HELP plz!!"
date: 2006-09-21
forum: Packaging and Compiling Programs
---

### Post by Nectron on 2006-09-21
I'm trying to install GTK2 and its required dependencies..

I've installed Glib, but now when I tried to ./configure ATK, I get an error massege saying that I have an older version of GLib which should be removed.

```

checking for pkg-config... (cached) /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0...
*** 'pkg-config --modversion glib-2.0' returned 2.11.4, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

How can I resolve this problem?

Thanks in advance..

---

### Post by Dinerty on 2006-09-21
Is this post any help?

[http://www.ubuntuforums.org/showthread.php?t=245376&highlight=glib](http://www.ubuntuforums.org/showthread.php?t=245376&highlight=glib)

---

### Post by Nectron on 2006-09-21
Thanks for the reply..

I went to /usr/local/lib/glib-2.0

the only file there was glibconfig.h

Is this the directory where Glib 2.10.3 is installed?

I need to remove Glib2.10.3


Thanks again ;)

---

