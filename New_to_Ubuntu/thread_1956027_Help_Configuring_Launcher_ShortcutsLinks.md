---
title: "Help Configuring Launcher Shortcuts/Links"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by Pinhound on 2012-04-10
EDIT: Wouldn't have thought this could've so easily fallen through the cracks, but I hacked a solution. I clobbered the original pgadmin3 file (located in /usr/bin/) with the new binary. That should seem easy, but the first time the pgadmin icon (the elephant) no longer appeared in the window switcher. Figuring I broke something, I replaced it. It still didn't return. A reboot eventually fixed this -- and it now functions as expected with the new binary simply copied over the old one. I don't like this solution. I still don't understand which component could've been restarted (instead of rebooting the system) and I had to find the original binary by sifting through the results of a find. Still uncertain how the system keeps its pointers (links?) to the various apps (or how to modify them).

Using Oneiric (11.10) and I've just upgraded pgAdmin III. Since I had to (or only knew how to) perform that upgrade manually, there is now a fully functional application (pgadmin3) safely configured deep within the /usr/lib/posgresql/ sub-directories. (And, if launched from a terminal window, works splendidly.)

Nevertheless, I cannot for the life of me figure out how to tell the launcher that pgadmin3 should be pointing to (?) this new install location. If I open the "Dash home" and type in 'pgadmin', it shows an icon (the elephant head) and will launch the application -- but, of course, it's loading the older version. If I right-click on the icon, it doesn't offer a context menu (with, say, a "properties" dialogue) to change the target.

Thanks in advance for all cycles.

---

