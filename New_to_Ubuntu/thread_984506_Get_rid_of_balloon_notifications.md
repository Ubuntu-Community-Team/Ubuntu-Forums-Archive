---
title: "Get rid of balloon notifications ?"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Drakkor on 2008-11-16
Yeah, when I log in, this always comes up,can I stop it from doing so ?
Thank  :)

---

### Post by ajgreeny on 2008-11-16
Agreed, slightly annoying, but there were other more pressing problems I had to deal with, such as the guest login screen resolution, which always lost the bottom panel on the monitor and would not remember the resolution I set when it was logged out, making the guest login just about useless for a casual user who is unlikely to know how to change the resolution.  I wonder if it is possible to turn of such notification in the configuration file, which is **/etc/dbus-1/system.d/nm-applet.conf in hardy**, which I'm on at the moment.  Have a look there and report back.

I eventually solved that by manually editing the xorg.conf file to include the display details from a previous version of xorg.conf (from dapper, I think) which included the resolutions possible for the monitor.  I though the xorg.conf file was now largely no longer needed for the setup of the system, but obviously it still can have a place, and manual edits still seem to work.

Touch wood, everything else seems great, though I only installed last night (a clean install on a second hard disk I keep for just such testing installs) and have yet to try all the packages I add to the basic installation.

---

### Post by spiderbatdad on 2008-11-16
some tooltips can be disabled with gconf-editor: Apps>>Panel>>Global>>Tool Tips Enabled. However, I don't think it will eliminate the nm-applet notification.

---

### Post by OrangeCrate on 2008-11-16
> **Drakkor said:**
> Yeah, when I log in, this always comes up,can I stop it from doing so ?
Thank  :)

Right click on the panel, and remove the notifications icon (the little twin computers). But then, of course, you won't be able to see the update icon, or any other notification icons, so it's up to you...

---

