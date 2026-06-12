---
title: "Ubuntu failed on update system"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by oc666 on 2011-09-05
Hey All,
I've update my system (11.04) yesterday:
```
sudo apt-get update && sudo apt-get upgrade
```
I'm getting the next output and can't login to the system via the gdm:
```
Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  gir1.2-freedesktop gir1.2-glib-2.0 linux-generic linux-headers-generic
  linux-image-generic python-gobject
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
187 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? dpkg: error processing libdbus-1-3 (--configure):
 libdbus-1-3:amd64 1.4.14-1ubuntu1 cannot be configured because libdbus-1-3:i386 is in a different version (1.4.12-4ubuntu2)
dpkg: error processing libffi6 (--configure):
 libffi6:amd64 3.0.11~rc1-2 cannot be configured because libffi6:i386 is in a different version (3.0.11~rc1-1)
dpkg: error processing libglib2.0-0 (--configure):
 libglib2.0-0:amd64 2.29.18-0ubuntu3 cannot be configured because libglib2.0-0:i386 is in a different version (2.29.16-0ubuntu3)
dpkg: dependency problems prevent configuration of libcolord1:
 libcolord1 depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libcolord1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of colord:
 colord depends on libcolord1 (>= 0.1.10); however:
  Package libcolord1 is not configured yet.
 colord depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing colord (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libgdk-pixbuf2.0-0 (--configure):
 libgdk-pixbuf2.0-0:amd64 2.24.0-1 cannot be configured because libgdk-pixbuf2.0-0:i386 is in a different version (2.23.5-3)
dpkg: dependency problems prevent configuration of libnotify4:
 libnotify4 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libnotify4 depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libnotify4 (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libpulse0 (--configure):
 libpulse0:amd64 1:0.99.3-0ubuntu1 cannot be configured because libpulse0:i386 is in a different version (1:0.99.2-0ubuntu2)
dpkg: dependency problems prevent configuration of libpulse-mainloop-glib0:
 libpulse-mainloop-glib0 depends on libglib2.0-0 (>= 2.16.0); however:
  Package libglib2.0-0 is not configured yet.
 libpulse-mainloop-glib0 depends on libpulse0 (>= 1:0.99.1); however:
  Package libpulse0 is not configured yet.
dpkg: error processing libpulse-mainloop-glib0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on libdbus-1-3 (>= 1.2.16); however:
  Package libdbus-1-3 is not configured yet.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus:
 dbus depends on libdbus-1-3 (>= 1.0.2); however:
  Package libdbus-1-3 is not configured yet.
 dbus depends on upstart-job; however:
  Package upstart-job is not installed.
  Package upstart which provides upstart-job is not configured yet.
 dbus depends on upstart (>= 0.6.3-6); however:
  Package upstart is not configured yet.
dpkg: error processing dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgirepository-1.0-1:
 libgirepository-1.0-1 depends on libffi6 (>= 3.0.4); however:
  Package libffi6 is not configured yet.
 libgirepository-1.0-1 depends on libglib2.0-0 (>= 2.29.7); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libgirepository-1.0-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libatspi2.0-0:
 libatspi2.0-0 depends on libdbus-1-3 (>= 1.1.1); however:
  Package libdbus-1-3 is not configured yet.
 libatspi2.0-0 depends on libglib2.0-0 (>= 2.22.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libatspi2.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of at-spi2-core:
 at-spi2-core depends on libatspi2.0-0 (>= 2.1.1); however:
  Package libatspi2.0-0 is not configured yet.
 at-spi2-core depends on libdbus-1-3 (>= 1.0.2); however:
  Package libdbus-1-3 is not configured yet.
 at-spi2-core depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing at-spi2-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of baobab:
 baobab depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 baobab depends on libglib2.0-0 (>= 2.29.14); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing baobab (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus-x11:
 dbus-x11 depends on dbus; however:
  Package dbus is not configured yet.
dpkg: error processing dbus-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-control-center1:
 libgnome-control-center1 depends on libglib2.0-0 (>= 2.29.14); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libgnome-control-center1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libglib2.0-0 (>= 2.29.13); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deja-dup:
 deja-dup depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 deja-dup depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
 deja-dup depends on libgnome-control-center1 (>= 1:2.91.2); however:
  Package libgnome-control-center1 is not configured yet.
 deja-dup depends on libnautilus-extension1 (>= 1:2.91); however:
  Package libnautilus-extension1 is not configured yet.
 deja-dup depends on libnotify4 (>= 0.7.0); however:
  Package libnotify4 is not configured yet.
dpkg: error processing deja-dup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserver1.2-15:
 libedataserver1.2-15 depends on libglib2.0-0 (>= 2.29.6); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libedataserver1.2-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel-1.2-28:
 libcamel-1.2-28 depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 libcamel-1.2-28 depends on libglib2.0-0 (>= 2.29.6); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libcamel-1.2-28 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-12:
 libebook1.2-12 depends on libcamel-1.2-28 (>= 3.1); however:
  Package libcamel-1.2-28 is not configured yet.
 libebook1.2-12 depends on libcamel-1.2-28 (<< 3.2); however:
  Package libcamel-1.2-28 is not configured yet.
 libebook1.2-12 depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 libebook1.2-12 depends on libglib2.0-0 (>= 2.28); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libebook1.2-12 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfolks25:
 libfolks25 depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libfolks25 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libfolks-telepathy25:
 libfolks-telepathy25 depends on libfolks25 (>= 0.6.0); however:
  Package libfolks25 is not configured yet.
 libfolks-telepathy25 depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libfolks-telepathy25 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnm-util2:
 libnm-util2 depends on libglib2.0-0 (>= 2.24.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libnm-util2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnm-glib4:
 libnm-glib4 depends on libdbus-1-3 (>= 1.0.2); however:
  Package libdbus-1-3 is not configured yet.
 libnm-glib4 depends on libglib2.0-0 (>= 2.22); however:
  Package libglib2.0-0 is not configured yet.
 libnm-glib4 depends on libnm-util2 (>= 0.8.998); however:
  Package libnm-util2 is not configured yet.
dpkg: error processing libnm-glib4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of empathy:
 empathy depends on libebook1.2-12 (>= 3.1.5); however:
  Package libebook1.2-12 is not configured yet.
 empathy depends on libfolks-telepathy25 (>= 0.5.2); however:
  Package libfolks-telepathy25 is not configured yet.
 empathy depends on libfolks25 (>= 0.6.0); however:
  Package libfolks25 is not configured yet.
 empathy depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 empathy depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
 empathy depends on libgnome-control-center1 (>= 1:2.91.2); however:
  Package libgnome-control-center1 is not configured yet.
 empathy depends on libnm-glib4 (>= 0.7.999); however:
  Package libnm-glib4 is not configured yet.
 empathy depends on libnotify4 (>= 0.7.0); however:
  Package libnotify4 is not configured yet.
 empathy depends on libpulse-mainloop-glib0 (>= 1:0.99.1); however:
  Package libpulse-mainloop-glib0 is not configured yet.
 empathy depends on libpulse0 (>= 1:0.99.1); however:
  Package libpulse0 is not configured yet.
 empathy depends on dbus-x11; however:
  Package dbus-x11 is not configured yet.
dpkg: error processing empathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libevince3-3:
 libevince3-3 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libevince3-3 depends on libglib2.0-0 (>= 2.25.1); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libevince3-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libevince3-3 (= 3.1.90.1-0ubuntu1); however:
  Package libevince3-3 is not configured yet.
 evince depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 evince depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 1:2.91); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebackend-1.2-1:
 libebackend-1.2-1 depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 libebackend-1.2-1 depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libebackend-1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-10:
 libecal1.2-10 depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 libecal1.2-10 depends on libglib2.0-0 (>= 2.28); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libecal1.2-10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book-1.2-11:
 libedata-book-1.2-11 depends on libebackend-1.2-1 (>= 3.1.5); however:
  Package libebackend-1.2-1 is not configured yet.
 libedata-book-1.2-11 depends on libebook1.2-12 (>= 3.1.5); however:
  Package libebook1.2-12 is not configured yet.
 libedata-book-1.2-11 depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 libedata-book-1.2-11 depends on libglib2.0-0 (>= 2.28); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libedata-book-1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal-1.2-13:
 libedata-cal-1.2-13 depends on libebackend-1.2-1 (>= 3.1.5); however:
  Package libebackend-1.2-1 is not configured yet.
 libedata-cal-1.2-13 depends on libecal1.2-10 (>= 3.1.5); however:
  Package libecal1.2-10 is not configured yet.
 libedata-cal-1.2-13 depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 libedata-cal-1.2-13 depends on libglib2.0-0 (>= 2.28); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libedata-cal-1.2-13 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libcamel-1.2-28 (= 3.1.5-0ubuntu2); however:
  Package libcamel-1.2-28 is not configured yet.
 evolution-data-server depends on libebackend-1.2-1 (>= 3.1.5); however:
  Package libebackend-1.2-1 is not configured yet.
 evolution-data-server depends on libebook1.2-12 (>= 3.1.5); however:
  Package libebook1.2-12 is not configured yet.
 evolution-data-server depends on libecal1.2-10 (>= 3.1.5); however:
  Package libecal1.2-10 is not configured yet.
 evolution-data-server depends on libedata-book-1.2-11 (>= 3.1.5); however:
  Package libedata-book-1.2-11 is not configured yet.
 evolution-data-server depends on libedata-cal-1.2-13 (>= 3.1.5); however:
  Package libedata-cal-1.2-13 is not configured yet.
 evolution-data-server depends on libedataserver1.2-15 (>= 3.1.5); however:
  Package libedataserver1.2-15 is not configured yet.
 evolution-data-server depends on libglib2.0-0 (>= 2.29.6); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 file-roller depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
 file-roller depends on libnautilus-extension1 (>= 1:2.91); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gdkpixbuf-2.0:
 gir1.2-gdkpixbuf-2.0 depends on libgdk-pixbuf2.0-0 (>= 2.23.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
dpkg: error processing gir1.2-gdkpixbuf-2.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtksourceview-3.0-0:
 libgtksourceview-3.0-0 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libgtksourceview-3.0-0 depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libgtksourceview-3.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-gtksource-3.0:
 gir1.2-gtksource-3.0 depends on gir1.2-gdkpixbuf-2.0; however:
  Package gir1.2-gdkpixbuf-2.0 is not configured yet.
 gir1.2-gtksource-3.0 depends on libgtksourceview-3.0-0 (>= 3.1.4); however:
  Package libgtksourceview-3.0-0 is not configured yet.
dpkg: error processing gir1.2-gtksource-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libindicate5:
 libindicate5 depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libindicate5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-indicate-0.6:
 gir1.2-indicate-0.6 depends on libindicate5 (= 0.5.91-0ubuntu3); however:
  Package libindicate5 is not configured yet.
dpkg: error processing gir1.2-indicate-0.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-nautilus-3.0:
 gir1.2-nautilus-3.0 depends on gir1.2-gdkpixbuf-2.0; however:
  Package gir1.2-gdkpixbuf-2.0 is not configured yet.
 gir1.2-nautilus-3.0 depends on libnautilus-extension1 (>= 1:2.91); however:
  Package libnautilus-extension1 is not configured yet.
dpkg: error processing gir1.2-nautilus-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gir1.2-notify-0.7:
 gir1.2-notify-0.7 depends on gir1.2-gdkpixbuf-2.0; however:
  Package gir1.2-gdkpixbuf-2.0 is not configured yet.
 gir1.2-notify-0.7 depends on libnotify4 (>= 0.7.3); however:
  Package libnotify4 is not configured yet.
dpkg: error processing gir1.2-notify-0.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of glib-networking:
 glib-networking depends on libglib2.0-0 (>= 2.29.18); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing glib-networking (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-3-2:
 libgnome-desktop-3-2 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libgnome-desktop-3-2 depends on libglib2.0-0 (>= 2.28.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libgnome-desktop-3-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libcolord1 (>= 0.1.10); however:
  Package libcolord1 is not configured yet.
 gnome-settings-daemon depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 gnome-settings-daemon depends on libglib2.0-0 (>= 2.29.14); however:
  Package libglib2.0-0 is not configured yet.
 gnome-settings-daemon depends on libgnome-desktop-3-2 (>= 3.1.4); however:
  Package libgnome-desktop-3-2 is not configured yet.
 gnome-settings-daemon depends on libnotify4 (>= 0.7.3); however:
  Package libnotify4 is not configured yet.
 gnome-settings-daemon depends on libpulse-mainloop-glib0 (>= 1:0.99.1); however:
  Package libpulse-mainloop-glib0 is not configured yet.
 gnome-settings-daemon depends on libpulse0 (>= 1:0.99.1); however:
  Package libpulse0 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libcolord1 (>= 0.1.10); however:
  Package libcolord1 is not configured yet.
 gnome-control-center depends on libgdk-pixbuf2.0-0 (>= 2.23.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 gnome-control-center depends on libglib2.0-0 (>= 2.29.14); however:
  Package libglib2.0-0 is not configured yet.
 gnome-control-center depends on libgnome-control-center1 (>= 1:3.1.4); however:
  Package libgnome-control-center1 is not configured yet.
 gnome-control-center depends on libgnome-desktop-3-2 (>= 3.1.2); however:
  Package libgnome-desktop-3-2 is not configured yet.
 gnome-control-center depends on libnm-glib4 (>= 0.8.998); however:
  Package libnm-glib4 is not configured yet.
 gnome-control-center depends on libnm-util2 (>= 0.8.998); however:
  Package libnm-util2 is not configured yet.
 gnome-control-center depends on libnotify4 (>= 0.7.3); however:
  Package libnotify4 is not configured yet.
 gnome-control-center depends on libpulse-mainloop-glib0 (>= 1:0.99.1); however:
  Package libpulse-mainloop-glib0 is not configured yet.
 gnome-control-center depends on libpulse0 (>= 1:0.99.1); however:
  Package libpulse0 is not configured yet.
 gnome-control-center depends on gnome-settings-daemon (>= 3.0.0); however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 nautilus depends on libglib2.0-0 (>= 2.29.14); however:
  Package libglib2.0-0 is not configured yet.
 nautilus depends on libgnome-desktop-3-2 (>= 3.0.0); however:
  Package libgnome-desktop-3-2 is not configured yet.
 nautilus depends on libnautilus-extension1 (>= 1:2.91); however:
  Package libnautilus-extension1 is not configured yet.
 nautilus depends on libnotify4 (>= 0.7.0); however:
  Package libnotify4 is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnux-1.0-0:
 libnux-1.0-0 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libnux-1.0-0 depends on libglib2.0-0 (>= 2.25.14); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libnux-1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libindicator3-6:
 libindicator3-6 depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 libindicator3-6 depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
dpkg: error processing libindicator3-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unity-services:
 unity-services depends on libgdk-pixbuf2.0-0 (>= 2.22.0); however:
  Package libgdk-pixbuf2.0-0 is not configured yet.
 unity-services depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
 unity-services depends on libindicator3-6; however:
  Package libindicator3-6 is not configured yet.
dpkg: error processing unity-services (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libunity-core-4.0-4:
 libunity-core-4.0-4 depends on libglib2.0-0 (>= 2.26.0); however:
  Package libglib2.0-0 is not configured yet.
 libunity-core-4.0-4 depends on libnux-1.0-0 (>= 1.6.0-0); however:
  Package libnux-1.0-0 is not configured yet.
 libunity-core-4.0-4 depends on libnux-1.0-0 (<< 1.6.2); however:
  Package libnux-1.0-0 is not configured yet.
 libunity-core-4.0-4 depends on unity-services (= 4.12.0-0ubuntu2); however:
  Package unity-services is not configured yet.
dpkg: error processing libunity-core-4.0-4 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping

```
I've try run *dpkg --configure -a* but I'm getting the same output.
I've try today to update the system again but I'm getting the same output.

Thanks in advance.

---

### Post by cariboo on 2011-09-05
Have you tried:

```
sudo apt-get -f install
```

---

### Post by ronacc on 2011-09-05
if he is updating from 11.04 to 11.10 don't he also have to run ```
 sudo apt-get dist-upgrade 
``` ?

---

### Post by oc666 on 2011-09-05
Hey
Thanks for your replies.
I've try both commands and stuff was installed.
But, now I'm getting other errors.
On *sudo apt-get -f install*:
> Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following extra packages will be installed:
  cpp-4.6 g++-4.6 gcc-4.6 lib32gcc1 libgcc1 libquadmath0 libstdc++6
  libstdc++6-4.6-dev
Suggested packages:
  gcc-4.6-locales g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  gcc-4.6-multilib libmudflap0-4.6-dev libgcc1-dbg libgomp1-dbg
  libquadmath0-dbg libmudflap0-dbg binutils-gold libstdc++6-4.6-doc
The following packages will be upgraded:
  cpp-4.6 g++-4.6 gcc-4.6 lib32gcc1 libgcc1 libquadmath0 libstdc++6
  libstdc++6-4.6-dev
8 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
170 not fully installed or removed.
Need to get 0 B/21.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? dpkg: error processing gcc-4.6-base (--configure):
 gcc-4.6-base:amd64 4.6.1-9ubuntu1 cannot be configured because gcc-4.6-base:i386 is in a different version (4.6.1-7ubuntu2)
Errors were encountered while processing:
 gcc-4.6-base
and when I run *sudo apt-get -f dist-upgrade*:
> Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages will be upgraded:
  cpp-4.6 eog g++-4.6 gcc-4.6 gir1.2-peas-1.0 lib32gcc1 libgcc1 libpeas-1.0-0
  libpeas-common libquadmath0 libstdc++6 libstdc++6-4.6-dev oneconf pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-raop pulseaudio-module-x11 pulseaudio-module-zeroconf
  pulseaudio-utils ttf-ubuntu-font-family ubuntu-mono usb-creator-common
  usb-creator-gtk zeitgeist-extension-fts
26 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
170 not fully installed or removed.
Need to get 0 B/25.3 MB of archives.
After this operation, 672 kB disk space will be freed.
Do you want to continue [Y/n]? dpkg: error processing gcc-4.6-base (--configure):
 gcc-4.6-base:amd64 4.6.1-9ubuntu1 cannot be configured because gcc-4.6-base:i386 is in a different version (4.6.1-7ubuntu2)
Errors were encountered while processing:
 gcc-4.6-base


Thanks for the help.

---

### Post by dino99 on 2011-09-05
how is /etc/apt/sources.list ?

deactivate third party repos (set only oneiric genuine repos)

---

### Post by oc666 on 2011-09-06
I think it happened because of this issue:
> gcc-4.6-base:amd64 4.6.1-9ubuntu1 cannot be configured because gcc-4.6-base:i386 is in a different version (4.6.1-7ubuntu2)
Recently, I've added the i386 to my repos: [http://ubuntuforums.org/showthread.php?p=11182004](http://ubuntuforums.org/showthread.php?p=11182004)

How could I clean up all my repos?

---

### Post by dino99 on 2011-09-06
search for orphans (gtkorphan) or

clean the whole system with bleachbit: but close all the opened apps first, then set carefully your prefs and use it as admin

( of course, deactivate all the related repo pointing to i386, into /etc/apt/sources.list)

---

### Post by oc666 on 2011-09-06
I don't have any GUI (can't login via gdm).

---

### Post by dino99 on 2011-09-06
then use nano or vim

sudo nano /etc/apt/sources.list

make the needed cleaning then save

then make some cleaning:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

 sudo apt-get install deborphan
sudo deborphan

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( wait till it end itself, can be long, dont stop it)

---

### Post by oc666 on 2011-09-07
> **dino99 said:**
> then use nano or vim

sudo nano /etc/apt/sources.list

make the needed cleaning then save

then make some cleaning:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

 sudo apt-get install deborphan
sudo deborphan

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
( wait till it end itself, can be long, dont stop it)


Doesn't help :confused:
> 

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages will be upgraded:
  apport apport-gtk at-spi2-core compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default cpp-4.6 eog file-roller firefox
  firefox-globalmenu firefox-gnome-support firefox-locale-en firefox-locale-he
  g++-4.6 gcc-4.6 gconf-defaults-service gconf2 gconf2-common gir1.2-atk-1.0
  gir1.2-gconf-2.0 gir1.2-gmenu-3.0 gir1.2-gtk-3.0 gir1.2-nautilus-3.0
  gir1.2-peas-1.0 gnome-control-center gnome-control-center-data
  gnome-desktop3-data gnome-games-common gnome-icon-theme gnome-keyring
  gnome-mahjongg gnome-menus gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-sudoku gnome-system-monitor
  gnomine grub-common grub-pc grub-pc-bin grub2-common
  gsettings-desktop-schemas gvfs gvfs-backends gvfs-bin gvfs-fuse info
  install-info jockey-common jockey-gtk lib32gcc1 lib32ncursesw5 lib32stdc++6
  lib32tinfo5 libatk-adaptor libatk1.0-0 libatk1.0-data libatspi2.0-0
  libdecoration0 libgail-3-0 libgail-3-common libgcc1 libgck-1-0 libgconf2-4
  libgcr-3-1 libgnome-control-center1 libgnome-desktop-3-2 libgnome-keyring0
  libgnome-menu-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtkmm-3.0-1
  libjtidy-java libnautilus-extension1 libncurses5 libncursesw5
  libpam-gnome-keyring libpeas-1.0-0 libpeas-common libperl5.12 libquadmath0
  libssl0.9.8 libstdc++6 libstdc++6-4.6-dev libtinfo5 libyelp0 mousetweaks
  nautilus nautilus-data ncurses-base ncurses-bin oneconf perl perl-base
  perl-modules pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-raop pulseaudio-module-x11
  pulseaudio-module-zeroconf pulseaudio-utils python-apport
  python-problem-report python3 python3-minimal python3.2 python3.2-minimal
  shared-mime-info thunderbird thunderbird-globalmenu
  thunderbird-gnome-support ttf-ubuntu-font-family ubuntu-mono
  usb-creator-common usb-creator-gtk vinagre vino yelp yelp-xsl
  zeitgeist-extension-fts
128 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
170 not fully installed or removed.
Need to get 0 B/103 MB of archives.
After this operation, 365 kB of additional disk space will be used.
Do you want to continue [Y/n]? Preconfiguring packages ...
dpkg: error processing gcc-4.6-base (--configure):
 gcc-4.6-base:amd64 4.6.1-9ubuntu2 cannot be configured because gcc-4.6-base:i386 is in a different version (4.6.1-7ubuntu2)
Errors were encountered while processing:
 gcc-4.6-base

I've clear the i386 but it still required the i386 package. Why??? :(

---

### Post by wgarcia on 2011-09-07
Remove build-essential (if you have it) and gcc-4.6-base, then try the upgrade again.

Reinstall afterwards if you need them.

---

