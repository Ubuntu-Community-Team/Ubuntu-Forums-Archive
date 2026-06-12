---
title: "All kinds of f-spot problems"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by griztown on 2008-08-03
I'm new to Ubuntu and trying to use f-spot to download pictures from my camera and then export selected photos to a gallery.  Here are my problems:

1)  I can't open f-spot from the Applications drop down list.  It gives me a fatal error:

```
An unhandled exception was thrown: F-Spot cannot find the Dbus session bus.  Make sure dbus is configured properly or start a new session for f-spot using "dbus-launch f-spot"

  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42

Assembly Version Information:

NDesk.DBus.Proxies (0.0.0.0)
gconf-sharp (2.20.0.0)
FSpot.Utils (0.0.0.0)
gdk-sharp (2.12.0.0)
gnome-vfs-sharp (2.20.0.0)
Mono.Addins (0.3.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
System (2.0.0.0)
Mono.Posix (2.0.0.0)
Cms (0.0.0.0)
FSpot.Core (0.0.0.0)
atk-sharp (2.12.0.0)
gtk-sharp (2.12.0.0)
Mono.Addins.Setup (0.3.0.0)
gnome-sharp (2.20.0.0)
glib-sharp (2.12.0.0)
f-spot (0.4.3.1)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-19-generic i686 unknown GNU/Linux

Distribution Information:

[/etc/debian_version]
lenny/sid

[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"


```

When I open a terminal and type "dbus-launch f-spot" it will work.  How do I fix it so that I can launch it from the Applications menu without opening a terminal?  I found several threads talking about this but none of them seemed to fix the problem.

2)  I can import images fine but when I tried to export a picture to a folder it crashed.

```
=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

There is a lot more code there obviously.  If it's needed I can post it.  Any help on this will be greatly appreciated.  My wife just gave birth and I'm eager to share these photos.

Thanks,
Ted

---

### Post by bobnutfield on 2008-08-03
It may not be related, but while Hardy was in beta and shortly after the final release, there were bugs in F-Spot that caused this kind of crash.  I myself had to remove the application and reinstall for it to work properly.

---

### Post by griztown on 2008-08-03
So I today I removed it and reinstalled it so it should be very fresh.

---

