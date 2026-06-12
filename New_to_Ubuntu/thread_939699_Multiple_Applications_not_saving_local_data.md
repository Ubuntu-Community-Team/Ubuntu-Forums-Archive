---
title: "Multiple Applications not saving local data"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Psmiffy on 2008-10-06
I am finding a lot of applications are not saving data correctly.
 Firefox does not save any preferences, and does even remember which page I came from, the back button is disabled.
 Supertux does not save any settings, sound, screen and does not save games.
 Gweled has lot its high scores list.
 Transmission Bittorrent Client does not save any preferences in between starts and closes.
 VLC Player does not save any preferences and settings.
 My Places menu does not remember any of my recent choices.

 None of the applications are crashing or causing error reports.

 I am using release 8.04

- Thank you so much for your assistance.
+ Update 2008/10/06
+ I managed to get a part solution by changing the owner of my files and changing the rights, but then after a day of working correctly it started to reset it self.
+
+ When I changed the settings with the chmod and chown, I got the message
+ at logon about the .dmrc file being ignored.
+
+ Thanks for your assistance.

---

### Post by Psmiffy on 2008-10-09
Hi

I managed to figure out what the problem was.  No disk space available.  I am somewhat confused though why the system did not notifify me of low storage space or anything, things just started going wrong.  Oh well, at least I will know for next time.

---

