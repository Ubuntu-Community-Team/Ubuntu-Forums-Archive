---
title: "How to start &quot;Xscreensaver&quot; automatically"
date: 2014-08-03
forum: New to Ubuntu
---

### Post by ray9 on 2014-08-03
I installed "xscreensaver" and I have to restart each session.  How can I get it start automatically?

---

### Post by Dennis N on 2014-08-03
It needs to be included in Autostarted applications. How that is done depends on whether you are using: Ubuntu, Xubuntu, Lubuntu... and what release (14.04? 12.04?)  So please advise.

Also any existing screensaver needs to be disabled or uninstalled.

---

### Post by ajgreeny on 2014-08-03
I am using xscreensaver in Xubuntu 12.04 and 14.04, not because it is needed but mainly as a way to show my photos regularly with the gl-slideshow screensaver available for it.

To do so I have added it to the startup applications of my sessions setup in xfce4 settings-manager, but in order to start the daemon but not the screensaver itself use the command **xscreensaver -no-splash**

As Dennis N says, remove any other screensaver you may already have by default, eg gnome-screensaver, and if your system uses lightlocker you should disable that as well or you may have conflicts.

---

### Post by ray9 on 2014-08-03
I'm using Ubuntu 14.04 LTS.

---

### Post by ajgreeny on 2014-08-03
So just click on the dash icon (top of launchbar) and type "startup" to find your startup application list and add **xscreensaver -no-splash** to the list of commands.

---

### Post by ray9 on 2014-08-04
Thank you.

---

