---
title: "Multiple Applications launchers after connecting a second monitor"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by skitnik on 2013-04-16
Hi everyone,

I'm using Ubuntu 12.04 on an HP Compaq Pro 6305 Microtower with an HP Compaq LA2006x display. After simultaneously connecting a second monitor (Samsung SyncMaster 2494), some dis- and reconnecting of it, and some playing around with AMD Catalyst Control Center I somehow managed to generate four Applications/Places launchers, four workspace switchers, four taskbars etc. How can I reverse this to one of each of these?

Many thanks in advance!
[ATTACH=CONFIG]241439[/ATTACH]

---

### Post by zobo90 on 2013-04-16
I managed to do that too (on Mint)! :D  But it was only on MATE.  I found that when I switched to other desktops, it didn't do it any more.  Also, every time I logged out and back in, it generated another task bar!  

I'm afraid I don't have a solution to this, as I needed a new computer anyway, so just reinstalled anything... but am also interested in learning why it did this! :D

---

### Post by skitnik on 2013-04-16
It's nice to hear I'm not the only person having experienced this. Is there a way to reinstall only a specific component (e.g., AMD Catalyst C Center) to solve this problem? Which would this component be: a driver, some package, anything else? Are the ACCC settings stored in some specific file which I can manually modify?
Any help would be highly appreciated.

---

### Post by winwah on 2013-04-17
i am not certain if this is going to help completely. i am not using an ATI/AMD video card but i did experience something close to this when i first connected my second display.

in "System Settings > Displays" you have a break down of the connected/detected displays that can be seen. at the bottom of the window there is a "Launcher Placement" option. you can specify where the launcher is docked, one on each, or just on a specific one. 

I hope that this might help.

---

### Post by skitnik on 2013-04-17
I removed the unwanted launchers/workspace switchers etc by "Alt+Right click", then choosing "Remove from panel". It seems almost a bit too easy but it worked.

---

