---
title: "Cairo-dock problems recently"
date: 2011-06-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-06-28
For the last few days I have been having problems with cairo-dock. There were some updates to it and ever since the cairo-dock package is having problems. I removed cairo-dock completely and left it a couple of days to see if any further updates arrived. Nope.
So I tried to re-install it and I get the error in the screenshot below.
I'm not aware of any held packages on my system :confused:
Has anybody experienced anything similar?
Thanks

---

### Post by garvinrick4 on 2011-06-28
Not with Cairo-dock but have had problems with docky not opening the package I intended.
Have had to set to not start up at boot and just wait til bugs worked out. Must be a common package could be "mono' I believe has Banshee broken and had tomboy notes
for quite a while down. I know docky uses mono-runtime. This will bump it up to front should be a user out there who has looked into this already.
##I have been using gnome3 in 11.10 do not remember if used a dock in 11.10 gnome unity interface.
##Below is held packages in oneiric using aptitude safe-upgrade from get go.
```
Log complete.
Aptitude 0.6.4: log report
Mon, Jun 27 2011 22:42:27 -0700

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 59 packages, and remove 0 packages.
893 kB of disk space will be used
===============================================================================
[HOLD, DEPENDENCIES] libedataserverui-3.0-0
[HOLD, DEPENDENCIES] libgtkhtml-4.0-0
[HOLD, DEPENDENCIES] libgtkhtml-4.0-common
[HOLD, DEPENDENCIES] libgtkhtml-editor-4.0-0
[HOLD, DEPENDENCIES] libnet-dns-perl
[HOLD, DEPENDENCIES] rhythmbox-plugin-cdrecorder
[HOLD, DEPENDENCIES] rhythmbox-plugins
[INSTALL, DEPENDENCIES] libdbusmenu-glib4
[INSTALL, DEPENDENCIES] libdbusmenu-gtk4
[HOLD] brasero
[HOLD] brasero-cdrkit
[HOLD] brasero-common
[HOLD] eog
[HOLD] evince
[HOLD] evince-common
[HOLD] evolution
[HOLD] evolution-common
[HOLD] evolution-data-server
[HOLD] evolution-data-server-common
[HOLD] evolution-exchange
[HOLD] evolution-plugins
[HOLD] gnome-control-center
[HOLD] gnome-desktop3-data
[HOLD] gnome-orca
[HOLD] gnome-panel
[HOLD] gnome-panel-data
[HOLD] gnome-screensaver
[HOLD] gnome-settings-daemon
[HOLD] gnome-shell
[HOLD] gvfs
[HOLD] gvfs-backends
[HOLD] gvfs-fuse
[HOLD] libalgorithm-diff-xs-perl
[HOLD] libapparmor-perl
[HOLD] libapt-pkg-perl
[HOLD] libcairo-perl
[HOLD] libdigest-sha1-perl
[HOLD] libevolution
[HOLD] libglib-perl
[HOLD] libgtk2-perl
[HOLD] libhtml-parser-perl
[HOLD] libio-pty-perl
[HOLD] liblocale-gettext-perl
[HOLD] libnet-dbus-perl
[HOLD] libpango-perl
[HOLD] libpurple0
[HOLD] libsnmp15
[HOLD] libsub-name-perl
[HOLD] libterm-readkey-perl
[HOLD] libtext-charwidth-perl
[HOLD] libtext-iconv-perl
[HOLD] libuuid-perl
[HOLD] libwww-perl
[HOLD] libxml-parser-perl
[HOLD] nautilus
[HOLD] perl
[HOLD] perl-base
[HOLD] perl-modules
[HOLD] python-gconf
[HOLD] python-glade2
[HOLD] python-gnome2
[HOLD] python-gtk2
[HOLD] rhythmbox
[HOLD] seahorse

```

---

### Post by Quackers on 2011-06-28
Thanks garvinrick4, I've been using cairo-dock since first installing OO and it's been fine. Too many clicks without it :-)
I'll wait and see what appears and try installing it every so often :-)

---

### Post by lidex on 2011-06-29
> There were some updates to it and ever since the cairo-dock package is having problems. I removed cairo-dock completely and left it a couple of days to see if any further updates arrived.
Same here. Seems to be a dependency issue with cairo-dock 2.3.0~3-0ubuntu1 needing cairo-dock-plug-ins 2.3.0~3-0ubuntu1 which is not yet in the repos. Guess there's only three of us using/not using it:
[https://bugs.launchpad.net/ubuntu/+source/cairo-dock/+bug/801400](https://bugs.launchpad.net/ubuntu/+source/cairo-dock/+bug/801400)
[https://bugs.launchpad.net/ubuntu/+source/cairo-dock-plug-ins/+bug/799774](https://bugs.launchpad.net/ubuntu/+source/cairo-dock-plug-ins/+bug/799774)

---

### Post by trizrK on 2011-06-29
I suggest AWN. I switched to it from cairo-dock and i love it.:D

---

### Post by Quackers on 2011-06-30
Yes, on startup it says that as it can't find any plugins, it won't bother starting up :-)
I run AWN on another system but I prefer cairo dock.

---

### Post by lidex on 2011-06-30
> **Quackers said:**
> Yes, on startup it says that as it can't find any plugins, it won't bother starting up :-)
I run AWN on another system but I prefer cairo dock.

Yep. That's what I had originally so I uninstalled all the cairo-dock packages and now it won't install.

---

### Post by Quackers on 2011-06-30
Me too :-)
I've got worse problems now though.
I re-installed OO because of unrelated problems and now I've got an unusable gnome-shell and a Unity desktop that won't do what I tell it to :-)
It's a laugh!

---

### Post by Quackers on 2011-07-06
It's just been fixed :-)
It's installable again now.

---

### Post by lidex on 2011-07-06
Good stuff. I gotta wonder though how that situation came about in the first place.

---

### Post by Quackers on 2011-07-06
It's happened before with cairo-dock that a package (last time I believe it was plugins) lagged behind.

---

### Post by 23dornot23d on 2011-09-02
This may be happening again ..... my plugins are not appearing anymore in Cairo-dock ....

after tonights dist-upgrade ...... 0 packages to upgrade now ......

But Cairo Dock is not working as I like it and every now and then as I select cairo-dock it throws me
out of the shell .......... to 2D ..... 



Will see what I have loaded now ... 2.4.0 xxxx now ....

[[COLOR=Red]**SCREENSHOT**[/COLOR]]("http://img9.imageshack.us/img9/6584/cairodock.jpg")

( I added the cairo ppa after doing the upgrades to fix the problem .... ) 
but even though the versions look ok ...... there are no plugins displaying ....

[[COLOR=Red]**SCREENSHOT 2**[/COLOR]]("http://img847.imageshack.us/img847/8439/noaddonsplugins.jpg")

Cairo dock works in KDE .......as I just found out ....... but not in Gnome-Shell anymore ..... weird

---

