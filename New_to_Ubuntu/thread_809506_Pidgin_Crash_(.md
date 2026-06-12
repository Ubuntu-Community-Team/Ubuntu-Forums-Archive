---
title: "Pidgin Crash :("
date: 2008-05-27
forum: New to Ubuntu
---

### Post by damonjablons on 2008-05-27
Hey,

I've posted this on the forum, under the Desktop section, but unfortunately it didn't get any attention, nor did the bug report I filed.

**My problem is:**

Whenever I open Pidgin, the program starts and connects to my networks, then loads all of my buddies.  Promptly after that, it crashes and I have to "Force Quit" the application.

Please help, thank you.

---

### Post by cheesypoof on 2008-05-27
You might want to disable all of your accounts in Pidgin first, so that they do not automatically login. Then you can login 1 by 1 and see which might be causing problems. If after all of this you still can't find a solution, download a different messenger program.

---

### Post by natman on 2008-05-27
Ya i know exactly what you mean, i have a feeling its got to do with the desktop, you using compiz/gnome KDE effects KDE4? also have you extra plugins on pidgin working?
My advice if you have the plugings
[HTML]cd /home/user/
mv ./.purple ./backup_purple[/HTML]
That will just rmove your pidgin profiles and puts them in a backup ( so you can still use them at another time. Then try using pidgin again see if it works afresh then add things back in piece by piece.
Hope that helps:)

---

### Post by damonjablons on 2008-05-27
If Pidgin automatically starts up and crashes with my AIM account auto logging in (my only account), how do I disable it without having the program open and crash!?

---

### Post by damonjablons on 2008-05-27
> **natman said:**
> Ya i know exactly what you mean, i have a feeling its got to do with the desktop, you using compiz/gnome KDE effects KDE4? also have you extra plugins on pidgin working?
My advice if you have the plugings
[HTML]cd /home/user/
mv ./.purple ./backup_purple[/HTML]
That will just rmove your pidgin profiles and puts them in a backup ( so you can still use them at another time. Then try using pidgin again see if it works afresh then add things back in piece by piece.
Hope that helps:)

This worked perfectly, thank you for the help!

---

