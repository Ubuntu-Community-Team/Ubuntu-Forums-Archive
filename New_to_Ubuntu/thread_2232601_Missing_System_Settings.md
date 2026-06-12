---
title: "Missing System Settings"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-07-03
I am missing a number System Settings - see attached.  I guess there is a terminal command to re-set System Settings so I have all the default icons.  Appreciate any help.

---

### Post by bapoumba on 2014-07-03
> **Quarkrad said:**
> .. - see attached..
Sorry, but it's missing :)

---

### Post by deadflowr on 2014-07-03
well, it's part of a package either
gnome-control-center = Should be for precise -ish
gnome-control-center-unity = Middle release aka raring/saucy
unity-control-center  = Should be for trusty -ish

Depending on which Ubuntu version you have installed.
Maybe try a reinstall.

---

### Post by Quarkrad on 2014-07-03
Silly me(!) - sorry.  I'm running 14.04 in flashback mode.

---

### Post by krishna.988 on 2014-07-03
[FONT=microsoft sans serif]Try this command:[/FONT]

[FONT=impact]sudo apt-get install ubuntu-desktop

[FONT=microsoft sans serif]It should work fine[/FONT]
[/FONT][FONT=courier new][/FONT]

---

### Post by deadflowr on 2014-07-03
Installing ubuntu-desktop metapackage won't help fix gnome-flashback.;)
However the package should be gnome-control-center for gnome-ishnesses, instead of unity-control-center.
I'm not sure but in the older version it has/had a separate package called gnome-control-center-data.

Perhaps try re-installing both of those.

---

### Post by Quarkrad on 2014-07-03
**sudo apt-get install gnome-control-center** and **sudo apt-get install gnome-control-center-data** had no effect.  I logged out of flashback and into unity (icons still missing).  I tried **sudo apt-get install unity-control-center** and they all came back.  Logged out and back into flashback and they are all still there.  Many thanks.

---

### Post by cigtoxdoc on 2014-09-19
Install unity-control-center is correct reply for 14.04 64-bit.  I ran into problem when I needed to remove an "experimental" copy of evolution and return to evolution 3.10.4.  You cannot do this w/o takingout some parts of unity desktop.  Do not know why programs cannot be removed w/o taking out critical parts of the OS.

John

---

