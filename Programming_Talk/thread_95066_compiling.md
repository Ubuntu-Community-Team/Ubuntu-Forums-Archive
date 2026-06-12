---
title: "compiling"
date: 2005-11-25
forum: Programming Talk
---

### Post by akurashy on 2005-11-25
i'm not much of a compiler, but i want to more, more deep to linux and etc etc, I'm getting this error while compiling epiphany

checking for DEPENDENCIES... configure: error: Package requirements (  glib-2.0 >= 2.8.0                gtk+-2.0 >= 2.8.3               libxml-2.0 >= 2.6.12            libxslt >= 1.1.7                libgnomeui-2.0 >= 2.6.0  libglade-2.0 >= 2.3.1            gnome-vfs-2.0 >= 2.9.2                  gnome-vfs-module-2.0            gconf-2.0               gnome-desktop-2.0 >= 2.9.91  libstartup-notification-1.0              libgnomeprint-2.2 >= 2.4.0  libgnomeprintui-2.2 >= 2.4.0             ) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the DEPENDENCIES_CFLAGS and DEPENDENCIES_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

---

### Post by Roptaty on 2005-11-25
Basically you need to install all the dev packages of the packages listed, but instead of trying to compile epiphany you could select an easier application to compile. For instance: You could try to compile/install xchat, irssi, gaim, xmms, beep-media-player or mplayer.

---

### Post by akurashy on 2005-11-25
i already compiled

xchat 2.6.0
gaim2cvs
mplayer
gimp 2.3.5

i see i need the latest gnome things and some other things =/

---

### Post by fct on 2005-11-26
Installing the metapackage gnome-core-devel will make your life easier when compiling gnome apps.

---

