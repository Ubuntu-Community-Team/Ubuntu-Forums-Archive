---
title: "User environment and other losses after crash"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by The.Justinian on 2008-10-23
Hi,

On about week 2 with Ubuntu with my thinkpad.  About everything working great, until today.

System crash in the middle of an update, after a recovery mode trip got booting and functions back up, but two problems:

GUI filebrowser won't open windows.
My user environment (EG, my desk, my personal panels, and so on isn't loading on boot.

Steps to take to correct this appreciated.

Cheers.

---

### Post by Hexagoon on 2008-10-23
Grab a terminal and try these commands to get your session back on track:

```
sudo dpkg-reconfigure nautilus
sudo dpkg-reconfigure gnome-session
```

Good luck!

Edit: This is only if X is running properly but you just get a empty desktop. Is it like that? Or isn't even X loading?

---

### Post by The.Justinian on 2008-10-23
desk, locations, user changes to panels not loading.
Filesystem browser not loading. (is this called x?)

did the terminal commands...no immediate effect.  Reboot?
We'll see if there's a restore after that.
Thanks,Cheers;

Justinian.

---

### Post by The.Justinian on 2008-10-23
Well,
After reboot, changes from the last session are coming through, but the file browser still won't load (directions to reinstall?), and my old desktop is still nowhere to be found.

I'm posting from the system with the troubles, so it is...working.  But without the ability to put files in a folder (desktop or no), its functionality is limited.

---

### Post by The.Justinian on 2008-10-24
So...bump for great justice.  In 24 hours I'll just to a reinstall unless a simpler solution is acquired.  Though, with Ubuntu, it's not like that's a huge undertaking.

---

