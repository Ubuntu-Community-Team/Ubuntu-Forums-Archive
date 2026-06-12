---
title: "tightvncviewer -listen on ubuntu 5.10"
date: 2005-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by tasca on 2005-08-22
Hi, howto tightvncviewer -listen?

tasca@softsul:~$ vncviewer -listen
vncviewer -listen: Listening on port 5500 (flash port 5400)
vncviewer -listen: Command line errors are not reported until a connection comes in.
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  45 (X_OpenFont)
  Serial number of failed request:  7
  Current serial number in output stream:  7
tasca@softsul:~$

in beatrix(ubuntu hoary) it functions perfect.

ubuntu 5.10 breezy
kernel Linux softsul 2.6.12-7-k7 #1 Fri Aug 19 13:46:31 UTC 2005 i686 GNU/Linux
Gnome 2.11
nvidia geforce2 mx 200

somebody can help me?

force and illumination

tasca...

---

### Post by thomsuey on 2005-10-26
See [https://bugzilla.ubuntu.com/show_bug.cgi?id=8376]("https://bugzilla.ubuntu.com/show_bug.cgi?id=8376")

"> Needed font is present in gsfonts-x11 package.

Confirmed. Works after installing gsfonts-x11"

I installed this package, rebooted, and all is well.  Tested connection with Windows UltraVNC Server.

---

