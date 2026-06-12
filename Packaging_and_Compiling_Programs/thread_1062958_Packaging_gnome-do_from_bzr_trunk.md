---
title: "Packaging gnome-do from bzr trunk"
date: 2009-02-07
forum: Packaging and Compiling Programs
---

### Post by amrlima on 2009-02-07
Hi,

I'm packaging gnome-do from trunk and I get the following error at compilation time (using pbuilder):

```
checking for NOTIFY_SHARP... configure: error: Package requirements (notify-sharp) were not met:

No package 'notify-sharp' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables NOTIFY_SHARP_CFLAGS
and NOTIFY_SHARP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I think I have all build dependencies: Any thing I can do about it? Thanks!
```

Build-Depends: debhelper (>= 7), 
	       autotools-dev,
	       cdbs,
	       dpatch, 
	       mono-gmcs (>= 1.1.8), 
	       c-sharp-2.0-compiler, 
               autotools-dev, 
	       libndesk-dbus1.0-cil, 
	       libndesk-dbus-glib1.0-cil, 
	       libgconf2.0-cil,
	       libgnome2.0-cil,
	       libglade2.0-cil,
	       libglib2.0-cil,
	       libgnomedesktop2.20-cil,
	       libgnome-keyring1.0-cil,
	       libgnome-vfs2.0-cil,
	       gtk-sharp2-gapi,
	       librsvg2-2.18-cil,
	       libmono-addins0.2-cil,
	       libmono-addins-gui0.2-cil,
	       libmono-cairo2.0-cil
	       libnotify0.4-cil,
	       libnotify-dev,
	       monodoc-notify-sharp-manual,
	       libwnck2.20-cil,
	       automake,
	       autoconf,
	       pkg-config,
	       libglib2.0-cil,
	       libgdk-pixbuf-dev,
	       libgtkglextmm-x11-dev,
	       libgtk2.0-cil,
	       cli-common-dev (>= 0.5.7),
	       intltool,
	       libglib2.0-dev,
	       libgtk2.0-dev
```

---

### Post by zekopeko on 2009-02-07
you could ask in #gnome-do on irc.freenode.net.

---

