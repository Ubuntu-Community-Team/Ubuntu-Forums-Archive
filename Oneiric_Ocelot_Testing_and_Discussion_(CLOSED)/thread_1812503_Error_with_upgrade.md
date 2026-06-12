---
title: "Error with upgrade"
date: 2011-07-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mrinsult2000 on 2011-07-26
I just upgraded from a fresh load of 11.04 to 11.10 by running update-manager -d.

Everything appeared to update with no issues.

It comes up to the log in menu, I hit my username, the log in menu goes away and nothing ever happens, blank screen.  Once this happens I have to drop to console and reboot.

If I hit Other, I can at least enter a username and password, and choose a desktop environment.  Gnome, and Ubuntu both fail, but I am able to log in with Ubuntu 2-D.

Anyone have any ideas on this one?  Anything I could do to make Gnome work.  Only thing I can think of that caused this was during the upgrade, it asked me to pick LightDM or GDM, for which I chose LightDM.

Thanks!

---

### Post by mrinsult2000 on 2011-07-26
For what its worth, I may have fixed this.
After logging into the Ubuntu 2-D desktop, I ran:

sudo apt-get install gnome-shell

After that finished, I ran the two following commands

sudo apt-get remove gnome-accessibility-themes
sudo apt-get install gnome-themes-standard

Rebooted, Chose my User, Gnome as my session, and was able to login fine.  Gnome3 appears to be functional at the very least.

---

