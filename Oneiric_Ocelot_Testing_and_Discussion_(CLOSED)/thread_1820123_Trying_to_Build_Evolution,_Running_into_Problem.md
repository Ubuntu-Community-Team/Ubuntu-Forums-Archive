---
title: "Trying to Build Evolution, Running into Problem"
date: 2011-08-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-08-07
I have no other choice and need to use evolution-exchange with Evolution; however, the current Oneiric version is broken, so I have to build it from scratch. I'm using the jhbuild mechanism and have solved many of the problems that have already crept-up, but can't seem to find any assistance for this one... any ideas?

```

/usr/bin/ld: ./.libs/libdbus-gtool.a(dbus-gidl.o): undefined reference to symbol 'g_boxed_type_register_static'
/usr/bin/ld: note: 'g_boxed_type_register_static' is defined in DSO /opt/gnome2/lib/libgobject-2.0.so so try adding it to the linker command line
/opt/gnome2/lib/libgobject-2.0.so: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[4]: *** [dbus-bash-completion-helper] Error 1
make[4]: Leaving directory `/home/bryan/cvs/gnome2/dbus-glib-0.92/dbus'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/bryan/cvs/gnome2/dbus-glib-0.92/dbus'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/bryan/cvs/gnome2/dbus-glib-0.92/dbus'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bryan/cvs/gnome2/dbus-glib-0.92'
make: *** [all] Error 2
*** Error during phase build of dbus-glib: ########## Error running make   *** [26/74]

```

Thanks, in-advance, community!

EDIT:
56 views and no thoughts? Really?

---

