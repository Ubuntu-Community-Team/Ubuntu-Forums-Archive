---
title: "upgrade from 11.04 to 11.10 Beta has corrupt desktop"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bsmith1051 on 2011-09-07
I had a relatively vanilla install of 11.04 (Unity desktop) which I just upgraded to 11.10 beta using the online process, i.e., I opened a command prompt and entered 'update-manager -d'.  The install went smoothly and there were no error messages.

After reboot, however, when i logged-in there's no apps or menus?  my desktop files are still there but there's no pop-up shortcuts, and across the top of the screen I only have the Nautilus drop-downs -- File, Edit, View, Go, Bookmarks, Help.  Also, about a minute after logging-in there was a crash report which opened FF, else I wouldn't have been able to get online to post this question!  (Now, for cya, I windowed the FF app and drag/dropped a desktop shortcut to this forum.)

After posting this I'm going to try ALT-F1 to get the command-line again, then force a shutdown/reboot.  Hopefully it's all just a one-time glitch? But if not, how do I reset the Unity desktop or config?

---

### Post by bsmith1051 on 2011-09-07
Good news.  After reboot the desktop has loaded correctly.  Hopefully the bug report (Launchpad) will help identify the initial error.  I doubt many users would know how to use ALT-F1?

Also, in poking around the new OS I found that the graphics is 'unknown' so maybe that's the problem.  Of course, I have an Nvidia 8300 IGP so it's nothing unusual.

**UPDATE** Discovered that I was already running the Nvidia proprietary video-drivers so maybe the 'generic' System Info detects that as 'unknown'

---

