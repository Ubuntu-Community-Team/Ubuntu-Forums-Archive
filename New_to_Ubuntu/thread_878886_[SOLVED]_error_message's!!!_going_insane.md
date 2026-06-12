---
title: "[SOLVED] error message's!!! going insane"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Joshfan on 2008-08-03
have a new problem, when i login with user and password as soon as the desktop opens this comes up:



[IMG]http://i276.photobucket.com/albums/kk23/joshfantoo/erroratlogin.png[/IMG]



and if i go into settings and try to adjust the appearance this comes up:


[B] Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.[/B]


and last thing when i try to lock screen this comes up:

**** Message: Failed to connect to the D-BUS daemon: Failed to connect to socket /tmp/dbus-7RCcGwNAhW: Connection refused**

this all came about after I installed Ubuntu studio so went back and uninstalled it through synaptic and i still get the messages.

---

### Post by CatKiller on 2008-08-03
Haven't seen that for a while. I used to get it in Feisty every now and then. My themes and session start up programs didn't work when it happened. Logging out and logging back in again made it work fine again.

Are you still on Feisty Fawn (7.04)?

---

### Post by Joshfan on 2008-08-03
No i am using gutsy gibbon 7.10. but i think it has been solved, it started when i installed Ubuntu studio so went and uninstalled everything in add/remove and rebooted and know it works fine, although it says i do not have a dbus directory, and so i posted a question about that on [[COLOR="Blue"]launchpad[/COLOR]]("https://answers.launchpad.net/~dbyrns")

---

### Post by SunnyRabbiera on 2008-08-03
well I can see if ubuntu studio messed up your gnome, if it happens again you can try to wipe out your hidden gnome profile folders and see if it resets gnome to its original settings.

---

