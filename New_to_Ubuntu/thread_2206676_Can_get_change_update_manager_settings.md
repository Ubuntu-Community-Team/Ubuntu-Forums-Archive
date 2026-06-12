---
title: "Can get change update manager settings"
date: 2014-02-20
forum: New to Ubuntu
---

### Post by The Frenchman on 2014-02-20
tried to do a suggested partial upgrade but package is freezing it.I can't get into update manager settings to untick non ubuntu packages

[B].Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.[/B]
Comes up when I try to do a partial upgrade even though nothing else is open. and in terminal I get [B]"unable to lock the administration directory (var/lib/dpkg) is another process using it?"

[/B]Having looked through the forum I see partial upgrades are not to be trusted.

---

### Post by The Frenchman on 2014-02-20
Update manager is telling me software index is broken and I should run" sudo apt-get install -f" but when I do I get [COLOR=#000000] [/COLOR]**"unable to lock the administration directory (var/lib/dpkg) is another process using it?" **&#8203;again!

---

### Post by The Frenchman on 2014-02-20
Best to reinstall 12.04? as it's stuck in this mode

---

### Post by philinux on 2014-02-20
> **The Frenchman said:**
> Best to reinstall 12.04? as it's stuck in this mode

No not yet.

For ease just reboot the machine and try the sudo apt-get install -f command and post back any errors.

It should be fixable.

---

