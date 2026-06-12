---
title: "Using XRPD"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-05-08
So this tool sounds amazing, but how the hell do I use it?  The web site for it offers no instructions on how to use it, just technical data.  I got it installed fine by using sudo apt-get install xrdp, but past that all I get are denials for the connection through mstsc or rdesktop

[http://xrdp.sourceforge.net/](http://xrdp.sourceforge.net/)

---

### Post by cprofitt on 2008-09-21
ssh -X -C -c blowfish username@computer gnome-panel

Found this in another thread and it works great for my needs. No need for VNC or XRDP.

---

