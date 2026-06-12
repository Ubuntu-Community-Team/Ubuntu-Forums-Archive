---
title: "GLib-GIO-Message: Using the 'memory' GSettings backend. Your settings will not be sav"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by lkdsajf on 2013-07-19
Hello,

trying to write some GTK+-code. Since I needed GTask, I decided to upgrade GLib to the newest version, which is 2.37.4. Now when I run this program I made, it always outputs 
```
GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved.
```
I already looked around and 
```
dpkg-query -l libdconf0 dconf-gsettings-backend dconf-tools libdconf-dbus-1-0
```
yields
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  dconf-gsetting 0.12.0-0ubuntu simple configuration storage system - GSetti
ii  dconf-tools    0.12.0-0ubuntu simple configuration storage system - utilit
ii  libdconf-dbus- 0.12.0-0ubuntu simple configuration storage system - D-Bus 
ii  libdconf0      0.12.0-0ubuntu simple configuration storage system - runtim

```

So to me, it seems I've installed all packages I need in order to use this ... new dbus-backend to store some system settings...

Any hint would greatly be appreciated.

Regards,
Paul

EDIT: uninstalled dconf-tools in favor of dconf, also installed libdconf-dev and libdconf-dbus-1-dev, now
EDIT 2: Alright, I suppose this thread should be moved to "General Help".

---

### Post by joeedh on 2014-01-04
I had a similar problem, and ended up recompiling dconf from source.  I went through the [repository]("http://ftp.acc.umu.se/pub/gnome/sources/dconf/"), and found the newest one that supported my version of glib ([14]("http://ftp.acc.umu.se/pub/gnome/sources/dconf/0.14/"), in my case).

Download the .tar.xz file, extract it with: "tar -xJvf" (note the upper-case J), run "./configure" in the resulting directory, then "make", then "sudo make install prefix=/usr"

That did it for me.

---

