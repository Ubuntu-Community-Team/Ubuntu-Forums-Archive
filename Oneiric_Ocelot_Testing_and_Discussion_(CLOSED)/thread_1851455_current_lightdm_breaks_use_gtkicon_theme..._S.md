---
title: "current lightdm breaks use gtk/icon theme... :S"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tista on 2011-09-28
Guys,

Just now I've updated lightdm to 1.0.0-0ubuntu2, then it seems to break user defined configurations especially gtk theme and icon theme on gnome desktop environments...

What a hell ?!

So I had only a choice to go back to gdm...

Any ideas?

Regards.

---

### Post by dino99 on 2011-09-28
have installed it too but dont have seen sad effect yet; will you get it after logout/reboot ?
Maybe gnome-panel --replace or unity --reset ?

note: i'm using genuine packages now

---

### Post by tista on 2011-09-28
> **dino99 said:**
> have installed it too but dont have seen sad effect yet; will you get it after logout/reboot ?
Maybe gnome-panel --replace or unity --reset ?

note: i'm using genuine packages now

@dino99,

Yeah I've already rebooted 2 or 3 times... but had no luck... :sad:

And I've updated below packages as well:
```
Commit Log for Wed Sep 28 22:39:46 2011


Upgraded the following packages:
apport (1.23-0ubuntu1) to 1.23-0ubuntu2
apport-gtk (1.23-0ubuntu1) to 1.23-0ubuntu2
ca-certificates (20110502+nmu1ubuntu3) to 20110502+nmu1ubuntu4
ffmpeg (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
gir1.2-freedesktop (1.30.0-0ubuntu1) to 1.30.0-0ubuntu2
gir1.2-glib-2.0 (1.30.0-0ubuntu1) to 1.30.0-0ubuntu2
gir1.2-lightdm-1 (0.9.7-0ubuntu2) to 1.0.0-0ubuntu1
gnome-control-center (1:3.2.0-0ubuntu1) to 1:3.2.0-0ubuntu2
gnome-control-center-data (1:3.2.0-0ubuntu1) to 1:3.2.0-0ubuntu2
gnome-online-accounts (3.2.0-0ubuntu1) to 3.2.0.1-0ubuntu1
gnome-user-guide (3.2.0-0ubuntu1) to 3.2.0.1-0ubuntu1
gobject-introspection (1.30.0-0ubuntu1) to 1.30.0-0ubuntu2
libavcodec53 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
libavdevice53 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
libavfilter2 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
libavformat53 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
libavutil51 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
libgirepository-1.0-1 (1.30.0-0ubuntu1) to 1.30.0-0ubuntu2
libgirepository1.0-dev (1.30.0-0ubuntu1) to 1.30.0-0ubuntu2
libgnome-control-center1 (1:3.2.0-0ubuntu1) to 1:3.2.0-0ubuntu2
libgoa-1.0-0 (3.2.0-0ubuntu1) to 3.2.0.1-0ubuntu1
libjack-jackd2-0 (1.9.7~dfsg-1ubuntu1) to 1.9.7~dfsg-1ubuntu2
liblightdm-gobject-1-0 (0.9.7-0ubuntu2) to 1.0.0-0ubuntu1
liblightdm-gobject-1-dev (0.9.7-0ubuntu2) to 1.0.0-0ubuntu1
libpostproc52 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
libswscale2 (4:0.7.1-3ubuntu1) to 4:0.7.1-7ubuntu2
lightdm (0.9.7-0ubuntu2) to 1.0.0-0ubuntu1
python-apport (1.23-0ubuntu1) to 1.23-0ubuntu2
python-problem-report (1.23-0ubuntu1) to 1.23-0ubuntu2
ubuntu-mono (0.0.34) to 0.0.36
unity-lens-applications (0.4.10-0ubuntu1) to 0.4.10-0ubuntu2

Commit Log for Wed Sep 28 23:22:42 2011


Upgraded the following packages:
aptdaemon (0.43+bzr697) to 0.43+bzr697-0ubuntu1
aptdaemon-data (0.43+bzr697) to 0.43+bzr697-0ubuntu1
gir1.2-gnomedesktop-3.0 (3.2.0-0ubuntu1) to 3.2.0-0ubuntu2
gir1.2-lightdm-1 (1.0.0-0ubuntu1) to 1.0.0-0ubuntu2
gnome-desktop3-data (3.2.0-0ubuntu1) to 3.2.0-0ubuntu2
libgnome-desktop-3-2 (3.2.0-0ubuntu1) to 3.2.0-0ubuntu2
libgnome-desktop-3-dev (3.2.0-0ubuntu1) to 3.2.0-0ubuntu2
liblightdm-gobject-1-0 (1.0.0-0ubuntu1) to 1.0.0-0ubuntu2
liblightdm-gobject-1-dev (1.0.0-0ubuntu1) to 1.0.0-0ubuntu2
lightdm (1.0.0-0ubuntu1) to 1.0.0-0ubuntu2
python-aptdaemon (0.43+bzr697) to 0.43+bzr697-0ubuntu1
python-aptdaemon-gtk (0.43+bzr697) to 0.43+bzr697-0ubuntu1
python-aptdaemon.gtk3widgets (0.43+bzr697) to 0.43+bzr697-0ubuntu1
python-aptdaemon.gtkwidgets (0.43+bzr697) to 0.43+bzr697-0ubuntu1
```

regards.

---

### Post by tista on 2011-09-28
This issue seems to be related to this bug?:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/861398]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/861398")

---

### Post by dino99 on 2011-09-28
hm dont know about that report, as i've rebooted too and dont get trouble, but you may have some newer packages from ricotz i have not.

---

### Post by tista on 2011-09-29
@dino99,

Thanks for your reply...

Just now, a few minutes ago the fixed version 1.0.0-0ubuntu3 were released!! :P
After updating, exactly it fixes my issue. Thanks devs...

Regards.

---

