---
title: "Trying to get Java app to run at user login (using DEB installer)"
date: 2011-02-10
forum: Packaging and Compiling Programs
---

### Post by MrQuan on 2011-02-10
I've created a Java application at work that at first had no GUI and ran as a daemon.  My .deb package had this autostarting at boot by putting a script into /etc/init.d and used an update-rc.d command in my postinst script. All good~~

Well, the lastest version of this Java app includes some GUI elements (system tray and dialog boxes) and no longer autostarts because it's trying to start before X server is up, so it bombs out because it can't handle the graphical stuff until after x is running.

I was going to fix this in the init.d start up method but I've read that "upstart" is the latest and greatest I should be using ;-)

I'm struggled to find a decent tutorial for upstart that shows how I would start my app when the user logs in (it's no longer a daemon app, more user interactive).

Can anyone please point me in the right direction or give me a crash course?
Much appreciated :-)
Mr Quan

---

