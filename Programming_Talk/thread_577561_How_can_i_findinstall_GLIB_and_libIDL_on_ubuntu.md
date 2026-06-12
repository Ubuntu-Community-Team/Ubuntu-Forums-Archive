---
title: "How can i find/install GLIB and libIDL on ubuntu"
date: 2007-10-16
forum: Programming Talk
---

### Post by yinglcs2 on 2007-10-16
How can i check if I have GLIB and ilbIDL install? 

I am getting the following error when i run  "make -f client.mk build" for building firefox under ubuntu.



checking for GLIB - version >= 1.2.0... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for libIDL-config... no
checking for libIDL - version >= 0.6.3... no
*** The libIDL-config script installed by libIDL could not be found
*** If libIDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBIDL_CONFIG environment variable to the
*** full path to libIDL-config.
checking for libIDL-2.0 >= 0.8.0... Package libIDL-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libIDL-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libIDL-2.0' found
configure: error: Library requirements (libIDL-2.0 >= 0.8.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

---

### Post by MicahCarrick on 2007-10-16
Find out if you have glib and not just glib-2.0

```
pkg-config --modversion glib
```

On my system, I have glib 1.2.10 and 2.14.1

To compile programs using the older version of glib, you must have the glib 1.2 development package installed: libglib1.2-dev

So, try this:

```
sudo aptitude install libglib1.2-dev libglib2.0-dev libidl-dev
```

---

### Post by yinglcs2 on 2007-10-16
Thank you.

I ran your command, but I get this following output:
```

 $ pkg-config --modversion glib
sh: glib-config: not found
sh: glib-config: not found
sh: glib-config: not found

```

---

