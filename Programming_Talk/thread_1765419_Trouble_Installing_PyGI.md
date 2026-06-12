---
title: "Trouble Installing PyGI"
date: 2011-05-23
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-05-23
Hi,

I couldn't find the Gdk.atom_intern() binding in my gi.repository, while others can, so i assume i may not have the latest version of PyGobject Introspection.

I've downloaded the latest version, but i am running in trouble during the configuration. Here is what it returned
```

$ ./configuration
...
...
checking for GLIB - version >= 2.24.0...
*** 'pkg-config --modversion glib-2.0' returned 2.24.2, but GLIB (2.28.6)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files

```

I am not sure as to how I should go about doing what is instructed. Could anyone guide me? (NB: I already have mailed this to the PyGtk/PyGobject mailing list but my experience is that such lists are silent...)

Thanks.
Benjamin

PS: should i have put this thread in the 'General Help' section?

---

### Post by jesuisbenjamin on 2011-05-25
I solved by own problem and [documented it]("http://gtk3lab.blogspot.com/2011/05/installing-gtk3-and-pygobject.html") for future reference.

---

