---
title: "Oneiric Alpha3 Default Login ?"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Bruce R on 2011-08-05
I am running the new oneiric-desktop-amd64 as a persistent USB created with StartUp Disk Creator and want to logoff and then back in as a 2D rather than Unity user but need to know the default login password in order to do so.
Can some kind soul tell me what it is ?  ;)

---

### Post by lisati on 2011-08-05
*Thread moved to **Ubuntu +1 (Oneiric Ocelot)**.*

---

### Post by drs305 on 2011-08-05
I believe you can log in as 'ubuntu' with a blank password.

---

### Post by xebian on 2011-08-05
Looks like it just logs you in Unity always though Unity2d or Gnome is selected (Installed gnome-shell).

---

### Post by Harry33 on 2011-08-05
> **xebian said:**
> Looks like it just logs you in Unity always though Unity2d or Gnome is selected (Installed gnome-shell).

This may be due to the bug in the package gnome-session_3.1.3-0ubuntu7.
Try to downgrade to the previous version 3.1.3-0ubuntu6.
Here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-session/3.1.3-0ubuntu6](https://launchpad.net/ubuntu/oneiric/+source/gnome-session/3.1.3-0ubuntu6)

And here is the bug (821477) report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/821477](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/821477)

---

