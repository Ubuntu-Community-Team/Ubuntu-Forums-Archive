---
title: "Gnome and Gnome classic still appearing in lightdm login menu"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by wgarcia on 2011-09-16
In one of the systems that I upgraded to 11.10 Beta 1, I had a bumpy upgrade (hit by the recent dependency bugs that were aborting the upgrade). I finished the upgrade manually (with apt-get updates and upgrades, clean, autoremove, autoclean) and everything seems OK except that I can still see two entries in the lightdm login screen that IMHO shouldn't be there: Gnome and Gnome Classic. In some other upgrades that I did these ones do not appear. I don't have gnome shell or its fallback installed. I tried purging and reinstalling lightdm and ubuntu-desktop but these entries are still there. I haven't tried to login into them. 

Could it be that Gnome 2 was not completely removed due to my upgrade problems? How can I make sure Gnome 2 is really gone?

Maybe it's just a matter of erasing some lines in the lightdm configuration files, but I've thought that purging this package would have also erased its configuration files.

---

### Post by Harry33 on 2011-09-16
> **wgarcia said:**
> In one of the systems that I upgraded to 11.10 Beta 1, I had a bumpy upgrade (hit by the recent dependency bugs that were aborting the upgrade). I finished the upgrade manually (with apt-get updates and upgrades, clean, autoremove, autoclean) and everything seems OK except that I can still see two entries in the lightdm login screen that IMHO shouldn't be there: Gnome and Gnome Classic. In some other upgrades that I did these ones do not appear. I don't have gnome shell or its fallback installed. I tried purging and reinstalling lightdm and ubuntu-desktop but these entries are still there. I haven't tried to login into them. 

Could it be that Gnome 2 was not completely removed due to my upgrade problems? How can I make sure Gnome 2 is really gone?

Maybe it's just a matter of erasing some lines in the lightdm configuration files, but I've thought that purging this package would have also erased its configuration files.

You may have gnome-fallback-session installed or at least the packages gnome-panel and metacity for Gnome Classic.

---

### Post by wgarcia on 2011-09-16
Right on the nail, removing those packages and now "Gnome" and "Gnome classic" are gone from the lightdm login session.

---

