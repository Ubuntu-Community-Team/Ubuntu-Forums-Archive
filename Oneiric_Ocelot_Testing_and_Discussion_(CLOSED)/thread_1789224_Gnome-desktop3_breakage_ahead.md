---
title: "Gnome-desktop3 breakage ahead"
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-23
The new gnome-desktop3 package will bring about some breakage.
This package set is inLaunchpad waiting (the state is new).
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-desktop3/3.1.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-desktop3/3.1.2-0ubuntu1)

Note that the name of the package libgnome-desktop-3-0 has been synced with Debian to libgnome-desktop-3-2.
Installing this will break gnome-shell, gnome-panel, gnome-control-center,
  gnome-settings-daemon and nautilus.

The old and new libgnome-desktop-3-x packages both depend on
gnome-desktop3-data, but different versions.

---

### Post by lucazade on 2011-06-26
Encountered this breakage trying to install nautilus and gnome-session from a minimal installation.
At the moment dependencies are not satisfied.

---

### Post by walt.smith1960 on 2011-06-26
Ooohhhhh yeah :p.  Before the latest upgrade killed it, the Gnome panel fallback mode  (or whatever it was called) is starting to look pretty good for the Gnome 2.x deprived.  Very similar to 11.04's "classic" mode and there's talk of there being a framework which makes it easy to write extensions to the shell.  My guess is that in less than the 10 years it took go get Gnome 2.xx to its current state, Gnome 3 will be sweet.

---

### Post by lucazade on 2011-06-26
> **walt.smith1960 said:**
> Ooohhhhh yeah :p.  Before the latest upgrade killed it, the Gnome panel fallback mode  (or whatever it was called) is starting to look pretty good for the Gnome 2.x deprived.  Very similar to 11.04's "classic" mode and there's talk of there being a framework which makes it easy to write extensions to the shell.  My guess is that in less than the 10 years it took go get Gnome 2.xx to its current state, Gnome 3 will be sweet.

a bit OT but LOL.. :)

when GNOME devs started to write v3 of their DE they "forgot" pc with limited gfx power (no 3D extensions and no composite available).
Unfortunately GnomeShell cannot run on pc without these specifications so Vuntz started a port of old gnome-panel to gtk3 to fill this "strange" lack. Obviously this requires time, also looking how much time it was required to gnomeshell to mature.

---

### Post by Harry33 on 2011-06-26
All the dependencies is met now.
You can install
- gnome-desktop3-data (3.1.2-0ubuntu1)
- libgnome-desktop-2-3 (3.1.2-0ubuntu1)
and then uninstall the old
- libgnome-desktop-3-0.

But at the same time all these must be upgraded to change the dependency from
libgnome-desktop-3-0 to libgnome-desktop-3-2:
- eog (3.0.2-1ubuntu3)
- gnome-control-center (3.0.2-1ubuntu5)
- gnome-control-center-data (3.0.2-1ubuntu5)
- gnome-panel (3.0.2-0ubuntu5)
- gnome-panel-data (3.0.2-0ubuntu5)
- gnome-screensaver (3.0.0-2ubuntu2)
- gnome-settigns-daemon (3.0.2-1ubuntu3b1)
- gnome-shell (3.0.2-1svn2)
- libgnome-control-center1 (3.0.2-1ubuntu5)
- libnautilus-extension1 (3.0.2-0ubuntu4)
- libpanel-applet-4-0 (3.0.2-0ubuntu5)
- nautilus (3.0.2-0ubuntu4)
- nautilus-data (3.0.2-0ubuntu4)

---

### Post by lucazade on 2011-06-26
thanks a lot.. As soon as will come back to home i'll try to update my box!

---

### Post by Harry33 on 2011-06-26
> **lucazade said:**
> thanks a lot.. As soon as will come back to home i'll try to update my box!

Right,
of course gnome-shell must now come from Oneiric official repos, because for example ricotz PPA's (testing and staging) still has the old dependency on libgnome-desktop-3-0.

---

### Post by Harry33 on 2011-06-26
Marking this thread as solved now.
I have upgraded my 32-bit and 64-bit setups and they work fine with the new gnome-desktop3.

---

### Post by MacUntu on 2011-06-26
Yeah, that was fun. Glad I had a network cable lying around for the upgrade. Thanks to Martin Pitt for fixing it. ;)

---

### Post by paul_in_london on 2011-06-26
Had to disable the **ricotz** ppa before I could reinstall **gnome-shell**.

Can't yet (re)install **nautilus-open-terminal**:

```
paul@oneiric:~$ sudo aptitude install nautilus-open-terminal
The following NEW packages will be installed:
  libgnome-desktop-3-0{ab} nautilus-open-terminal 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 157 kB of archives. After unpacking 1,212 kB will be used.
The following packages have unmet dependencies:
  libgnome-desktop-3-0: Depends: gnome-desktop3-data (= 3.0.2-2) but 3.1.2-0ubuntu1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libgnome-desktop-3-0 [Not Installed]               
2)     nautilus-open-terminal [Not Installed]             



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
paul@oneiric:~$
```

---

### Post by paul_in_london on 2011-06-27
In the **ricotz** ppa, **gnome-shell** now depends on **libgnome-desktop-3-2** instead of **libgnome-desktop-3-0** and can therefore be upgraded with that ppa enabled:

```
paul@oneiric:~$ dpkg -s gnome-shell
Package: gnome-shell
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 4064
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
**[COLOR="Red"]Version: 3.0.2+git20110626.e39e539e-0ubuntu1~11.10~ricotz0[/COLOR]**
Depends: gir1.2-atk-1.0 (>= 1.32), gir1.2-clutter-1.0 (>= 1.4),\
gir1.2-freedesktop (>= 0.10.6), gir1.2-gdkpixbuf-2.0,\
gir1.2-glib-2.0 (>= 0.9), gir1.2-gtk-3.0, gir1.2-json-glib-1.0,\
gir1.2-mutter-3.0, gir1.2-pango-1.0, gir1.2-telepathyglib-0.12,\
gir1.2-telepathylogger-0.2, gjs (>= 0.7.11), gnome-bluetooth (>= 3.0.0),\
libatk1.0-0 (>= 1.12.4), libc6 (>= 2.7), libcairo2 (>= 1.6.0),\ libcanberra0 (>= 0.2), libclutter-1.0-0 (>= 1.6.0), libcroco3 (>= 0.6.2),\
libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),\
libecal1.2-9 (>= 3.1.2), libedataserver1.2-14 (>= 3.1.2),\
libedataserverui-3.0-0 (>= 3.1.2), libgconf2-4 (>= 2.31.1),\
libgdk-pixbuf2.0-0 (>= 2.22.0), libgirepository-1.0-1 (>= 0.9.2),\
libgjs0b (>= 0.7.11), libglib2.0-0 (>= 2.28.0),\
[COLOR="Red"]**libgnome-desktop-3-2**[/COLOR] (>= 2.91.5), libgnome-menu2 (>= 2.27.92), libgstreamer0.10-0 (>= 0.10.20), libgtk-3-0 (>= 3.0.0), libical0 (>= 0.30), libmozjs185-1.0 (>= 1.8.5~hg20110306r6), libmutter0 (>= 3.0.0), libpango1.0-0 (>= 1.14.0), libpolkit-agent-1-0 (>= 0.99), libpolkit-gobject-1-0 (>= 0.94), libpulse-mainloop-glib0, libpulse0 (>= 0.9.23), libstartup-notification0 (>= 0.11), libtelepathy-glib0 (>= 0.15.0), libtelepathy-logger2 (>= 0.2.0), libx11-6, libxfixes3 (>= 1:5.0), libxml2 (>= 2.7.4), dconf-gsettings-backend | gsettings-backend, gconf2 (>= 2.28.1-2), libdconf0 | gsettings-backend, gnome-settings-daemon (>= 2.91.5.1), gsettings-desktop-schemas (>= 0.1.7), gnome-icon-theme-symbolic (>= 2.91), gir1.2-gconf-2.0, gir1.2-gkbd-3.0, gir1.2-gnomebluetooth-1.0, gir1.2-networkmanager-1.0, gir1.2-polkit-1.0, gir1.2-upowerglib-1.0, python, pkg-config, mesa-utils
Recommends: gnome-control-center
Breaks: gnome-control-center (<< 1:3.0)
Description: graphical shell for the GNOME desktop
 The GNOME Shell redefines user interactions with the GNOME desktop.
 In particular, it offers new paradigms for launching applications,
 accessing documents, and organizing open windows in GNOME. Later, it
 will introduce a new applets eco-system and offer new solutions for
 other desktop features, such as notifications and contacts
 management. The GNOME Shell is intended to replace functions handled
 by the GNOME Panel and by the window manager in previous versions of
 GNOME. The GNOME Shell has rich visual effects enabled by new
 graphical technologies.
Homepage: http://live.gnome.org/GnomeShell
Original-Maintainer: Gustavo Noronha Silva <gustavo.noronha@collabora.co.uk>
paul@oneiric:~$
```

---

