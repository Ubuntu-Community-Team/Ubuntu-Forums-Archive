---
title: "Exporting From Evolution And Thunderbird"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by BarfBag on 2008-07-17
A friend of mine is in a bit of a predicament.  He's using Dapper Drake, and desperately needs to upgrade.  This upgrade can't be done from the update manager for a couple reasons.  1.  When this system was first installed, Automatix was used.  2.  Setting aside all the upgrade problems Automatix is known to cause, the repositories are slug slow.  Upgrading would take days.  A clean install must be done.

This friend has two e-mail clients - Evolution and Thunderbird.  He used Evolution originally, but switched to Thunderbird after experiencing bazaar glitches.  There is e-mail he wants to save in both clients.  I haven't tried Evolution yet (instructions on how to export from Evolution and import back to it would be much appreciated), but I have made an attempt to export from Thunderbird.  Unfortunately, I suspect I made the problem worse.  I tried to copy the Thunderbird folder (out of the Home folder) onto a thumb drive, so I could later just replace the one in the existing system with it.  This didn't work, because it's write-protected.  It didn't even work through a root terminal, which puzzled me.  I then, being stupid, cut the folder and tried to paste it in the thumb drive once again.  Since it's write-protected, it didn't move.  It stayed cut, though.  I can no longer see the folder.  A restart didn't make it reappear.  I know it's still there because I can see it through the terminal.

Basically, I need to know how to export from Evolution and import back when the system is upgraded.  With Thunderbird, I need to know how to do the same.  Please help!

---

### Post by silkstone on 2008-07-17
I can't help with Evolution as I've never used it, but with Thunberbird you just need to **copy** the Mail folder which is buried under .mozilla-thunderbird (in Hardy, anyway).

You can then paste the contents of the Mail folder into the equivalent folder in the new install.

You own the Mail folders and there should be no problems copying them. You don't need to write to them - you're just trying to copy! I regularly back up the Mail folder to an external drive.

If you've 'cut' any of the Thunderbird folders then there may be a problem. Are they really still there? Can you still access them from Thunderbird?

---

### Post by BarfBag on 2008-07-17
> **silkstone said:**
> I can't help with Evolution as I've never used it, but with Thunberbird you just need to **copy** the Mail folder which is buried under .mozilla-thunderbird (in Hardy, anyway).

You can then paste the contents of the Mail folder into the equivalent folder in the new install.

You own the Mail folders and there should be no problems copying them. You don't need to write to them - you're just trying to copy! I regularly back up the Mail folder to an external drive.

If you've 'cut' any of the Thunderbird folders then there may be a problem. Are they really still there? Can you still access them from Thunderbird?

Oh yeah.  Everything can still be accessed from Thunderbird, so it's obviously still there.  I just can't see it.

---

### Post by BarfBag on 2008-07-17
Bump.

---

