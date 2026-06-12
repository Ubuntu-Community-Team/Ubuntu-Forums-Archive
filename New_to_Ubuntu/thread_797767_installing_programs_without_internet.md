---
title: "installing programs without internet???"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by mitar on 2008-05-17
Is there a way to install a program if I am not connected to the internet. Right now I am trying to install gnome ppp which is for dial up connection but I can not do it. While trying to install it shows the message: 

W: Failed to fetch [http://us.archives.ubuntu.com/.../gnome-ppp_0.3.23-1_i386.deb](http://us.archives.ubuntu.com/.../gnome-ppp_0.3.23-1_i386.deb)
Could not resolve 'us.archive.ubuntu.com'

Any help? or if there is an alternate way to set up dial-up connection?

---

### Post by arochester on 2008-05-17
"Install Applications in Ubuntu without Internet" at [http://planetoss.com/detail.php?id=13](http://planetoss.com/detail.php?id=13)

---

### Post by mitar on 2008-05-19
Does anyone know any other way? This one mantioned above is way too copmlicated

---

### Post by bubba_169 on 2008-05-19
Search for a .deb installation file using a computer thats connected to the net then use a flash drive or network etc to transfer it onto the computer you need it on. Dont forget you'll need to download the dependancies too if you're doing it this way! :)

---

### Post by mitar on 2008-05-19
what are the dependecies?

---

### Post by bubba_169 on 2008-05-19
Dependancies are other programs you must install so that another program can run. For example something written in python will need the python runtime libraries!

[http://http.us.debian.org/debian/pool/main/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb]("http://http.us.debian.org/debian/pool/main/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb")

Try installing this package on your computer and see what it asks for. You might already have everything it needs.

---

### Post by gerben1 on 2008-05-19
> **mitar said:**
> what are the dependecies?

```
sudo apt-cache show gnome-ppp
[sudo] password for gerben:
Package: gnome-ppp
Priority: optional
Section: universe/net
Installed-Size: 600
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Zak B. Elep <zakame@spunge.org>
Architecture: i386
Version: 0.3.23-1
[B]Depends: libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libfon
tconfig1 (>= 2.3.0), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.0), libgtk2
.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.14.4), libx11-6, libxcursor1 (>> 1.1.2), l           ibxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.26), libxrandr2, libx           render1, wvdial[/B]
Conflicts: resolvconf
Filename: pool/universe/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb
Size: 84046
MD5sum: 121507f8cd2b84709231a514b5fb6fde
SHA1: 0501e5fc1257124d35b9c449544dbca3315bf616
SHA256: fc8541de285797db930e80648f1cfc567c41297a80d524f44c341a60b77a5bb4
Description: modem internet connection tool for the GNOME Desktop
 GNOME PPP is an easy to use graphical dialup connection configuring
 and dialing tool with system tray icon support.
 .
 It uses GNOME/GTK+ for its graphical interface and integrates well
 in GNOME desktop environment, but it can be used in other environments.
 .
 It also uses WvDial dialer as its backend, providing simple configuration
 via config files. You can also use plain wvdial if you don't have X running.
 .
  Homepage: http://www.gnome-ppp.org/
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by mitar on 2008-05-19
> **bubba_169 said:**
> Dependancies are other programs you must install so that another program can run. For example something written in python will need the python runtime libraries!

[http://http.us.debian.org/debian/pool/main/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb]("http://http.us.debian.org/debian/pool/main/g/gnome-ppp/gnome-ppp_0.3.23-1_i386.deb")

Try installing this package on your computer and see what it asks for. You might already have everything it needs.

It worked. Thanks

---

