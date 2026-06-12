---
title: "Unable to compile gnome-panel on Ubuntu Intrepid"
date: 2009-01-16
forum: Packaging and Compiling Programs
---

### Post by frenkel on 2009-01-16
Hi,

I'm unable to compile gnome-panel on Ubuntu Intrepid.
This is what I ran:

```

$ sudo apt-get build-dep gnome-panel
$ apt-get source --compile gnome-panel

```

And it results in the following error:
```

make[4]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/icons/32x32'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/icons/32x32'
Making all in 48x48
make[4]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/icons/48x48'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/icons/48x48'
Making all in scalable
make[4]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/icons/scalable'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/icons/scalable'
make[4]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/icons'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/icons'
make[3]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/icons'
Making all in gnome-panel
make[3]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/gnome-panel'
/usr/bin/orbit-idl-2 -I /usr/share/idl/bonobo-2.0 -I /usr/share/idl/bonobo-activation-2.0 ../idl/GNOME_Panel.idl
orbit-idl-2 2.14.16 compiling
  mode, hide preprocessor errors, passes: stubs skels common headers 

Processing file ../idl/GNOME_Panel.idl
glib-mkenums    --fhead "#include <glib-object.h>\n" \
                        --fhead "#include \"panel-typebuiltins.h\"\n\n" \
                        --fprod "\n/* enumerations from \"@filename@\" */" \
                        --fprod "\n#include \"@filename@\"\n" \
                        --vhead "static const GEnumValue _@enum_name@_values[] = {" \
                        --vprod "  { @VALUENAME@, \"@VALUENAME@\", \"@valuenick@\" }," \
                        --vtail "  { 0, NULL, NULL }\n};\n\n" \
                        --vtail "GType\n@enum_name@_get_type (void)\n{\n" \
                        --vtail "  static GType type = 0;\n\n" \
                        --vtail "  if (!type)\n" \
                        --vtail "    type = g_enum_register_static (\"@EnumName@\", _@enum_name@_values);\n\n" \
                        --vtail "  return type;\n}\n\n" \
                ../gnome-panel/panel-enums.h ../gnome-panel/panel-types.h GNOME_Panel.h > panel-typebuiltins.c
glib-mkenums    --fhead "#ifndef __PANEL_TYPEBUILTINS_H__\n" \
                        --fhead "#define __PANEL_TYPEBUILTINS_H__ 1\n\n" \
                        --fhead "G_BEGIN_DECLS\n\n" \
                        --ftail "G_END_DECLS\n\n" \
                        --ftail "#endif /* __PANEL_TYPEBUILTINS_H__ */\n" \
                        --fprod "\n/* --- @filename@ --- */" \
                        --eprod "#define PANEL_TYPE_@ENUMSHORT@ @enum_name@_get_type()\n" \
                        --eprod "GType @enum_name@_get_type (void);\n" \
                ../gnome-panel/panel-enums.h ../gnome-panel/panel-types.h GNOME_Panel.h >  panel-typebuiltins.h
echo "#include \"panel-marshal.h\"" > panel-marshal.c && \
        /usr/bin/glib-genmarshal panel-marshal.list --body --prefix=panel_marshal >> panel-marshal.c
/usr/bin/glib-genmarshal panel-marshal.list --header --prefix=panel_marshal > panel-marshal.h
/usr/bin/make  all-recursive
make[4]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/gnome-panel'
Making all in libpanel-util
make[5]: Entering directory `/home/frank/Downloads/gnome-panel-2.24.1/gnome-panel/libpanel-util'
/bin/bash ../../libtool --tag=CC   --mode=compile cc -DHAVE_CONFIG_H -I. -I../.. -I. -I. -I../../gnome-panel -I../../gnome-panel/libpanel-util -DPANEL_DEBUG -DGNOMELOCALEDIR=\""/usr/share/locale"\" -DGLADEDIR=\"""\" -DICONDIR=\""/usr/share/gnome-panel/pixmaps"\" -DGMENU_I_KNOW_THIS_IS_UNSTABLE   -DORBIT2=1 -pthread -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/libgnome-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/gnome-desktop-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libglade-2.0 -I/usr/include/gnome-menus    -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare      -g -O2 -g -Wall -O2 -c -o panel-cleanup.lo panel-cleanup.c
mkdir .libs
 cc -DHAVE_CONFIG_H -I. -I../.. -I. -I. -I../../gnome-panel -I../../gnome-panel/libpanel-util -DPANEL_DEBUG -DGNOMELOCALEDIR=\"/usr/share/locale\" -DGLADEDIR=\"\" -DICONDIR=\"/usr/share/gnome-panel/pixmaps\" -DGMENU_I_KNOW_THIS_IS_UNSTABLE -DORBIT2=1 -pthread -I/usr/include/orbit-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pango-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gio-unix-2.0/ -I/usr/include/libgnome-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/gnome-desktop-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libglade-2.0 -I/usr/include/gnome-menus -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare -g -O2 -g -Wall -O2 -c panel-cleanup.c  -fPIC -DPIC -o .libs/panel-cleanup.o
../../libtool: eval: line 1322: unexpected EOF while looking for matching `"'
../../libtool: eval: line 1323: syntax error: unexpected end of file
make[5]: *** [panel-cleanup.lo] Error 1
make[5]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/gnome-panel/libpanel-util'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/gnome-panel'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1/gnome-panel'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/frank/Downloads/gnome-panel-2.24.1'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
Build command 'cd gnome-panel-2.24.1 && dpkg-buildpackage -b -uc' failed.
E: Child process failed

```

It doesn't matter which directory I'm in (I only want to build the applets), it always gives the same error.

Anybody know how to solve that?

---

