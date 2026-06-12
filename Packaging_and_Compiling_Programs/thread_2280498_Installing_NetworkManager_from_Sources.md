---
title: "Installing NetworkManager from Sources"
date: 2015-05-31
forum: Packaging and Compiling Programs
---

### Post by actionmystique on 2015-05-31
Environment:
--------------------
Ubuntu Server 15.04 with Gnome
All sources come from official git repositories

I have tried to compile and install NM 1.1.0-dev and all its plugins (applet, openconnect, openvpn, pptp and vpnc, all 1.0.2) over existing ubuntu packages that come with vivid.
I have configured NM with the following options:
./configure --enable-introspection=yes --prefix=/usr --sysconfdir=/etc --localstatedir=/var

The installations go without any glitch, except for vpnc (error during compilation).

I have a concern over a set of [related packages]("https://drive.google.com/file/d/0B5fXyIn0-GDFaTE4SHduQXV1LWs/view?usp=sharing") that are already installed with ubuntu and have discrepancies with the new manually compiled packages. I cannot remove the libnm-* and gir1.2-nmgtk packages because too many other packages depend on them.

What should be done here?

---

