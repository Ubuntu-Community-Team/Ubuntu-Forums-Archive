---
title: "can't login at all"
date: 2011-07-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mgsfan on 2011-07-21
ever since updating yesterday I can't login after rebooting.. I get the double login screen and then the login window disappears after clicking on my user name  and I'm stuck staring at the background wallpaper

seems like an update is crashing gdm or something since I see a line in the middle of my user name in the login window

---

### Post by cariboo on 2011-07-21
Select other, then type you user name and password to login. You only have to do this once, from then on you should be able to login normally.

---

### Post by cecilpierce on 2011-07-21
> **mgsfan said:**
> ever since updating yesterday I can't login after rebooting.. I get the double login screen and then the login window disappears after clicking on my user name  and I'm stuck staring at the background wallpaper

seems like an update is crashing gdm or something since I see a line in the middle of my user name in the login window

same thing happen to me, I waited about 3 minutes and the desk top finally came up the took 2 minutes to reboot, try waiting and see if it comes up or maybe goto recovery mode and update things, good luck !
:P

---

### Post by mgsfan on 2011-07-21
I can't click on other without the login window disappearing  and I've updated today and still nada...have'nt tried waiting to see what happens after the login goes away yet though



updated and tried again and still no go. If I click anywhere on screen while the login is up it crashes and once I click 3 times it goes poof for good..such an odd bug

---

### Post by dj_palindrome on 2011-07-22
I have a somewhat different problem. After the /run transition fiasco, I retrenched to a known-good snapshot, held back certain packages, then re-applied all updates in stages (never violating dependency rules). I was still OK until I updated base-files, initscripts, and mountall. Then the login screen never appeared again. The Plymouth logo eventually stopped spinning and the system hung at a black screen.
 
I really don't have enough to go on to take this to Launchpad (the developer's own systems are breaking; gcc-4.6 is producing compilation errors for packages whose maintainers don't use gcc-4.6 internally; and they seem to be in an *unusually* foul mood, which is saying something).

---

### Post by mgsfan on 2011-07-22
I've tried to login via lightdm instead of gdm using gnome and it just hangs on the background..if I use ubuntu I get to the desktop but it seems like gtk is crashing or something else is going on..and after I click around on the desktop it also goes poof and disappears I'm back to square 1 again

might just do a fresh install but hoping future updates fix this issue..

---

### Post by erkiha on 2011-07-23
I have same symptoms with lightdm. gdm works ok.

To switch between them I use ctrl+alt+f1, logon to terminal and:
sudo dpkg-reconfigure gdm. Then choose gdm or lightdm.

---

