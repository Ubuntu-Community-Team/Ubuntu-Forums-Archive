---
title: "No updates in update-manager"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by skroops on 2008-05-04
I installed the 8.04 RC the day before the final release, and since then I have had no update notifications and each time I start the update-manager I'm told that my system is up-to-date.

Has there really been no updates since last month or did something go wrong with my system?  Or is ubuntu now silently upgrading and install by default?

---

### Post by Oldsoldier2003 on 2008-05-04
> **skroops said:**
> I installed the 8.04 RC the day before the final release, and since then I have had no update notifications and each time I start the update-manager I'm told that my system is up-to-date.

Has there really been no updates since last month or did something go wrong with my system?  Or is ubuntu now silently upgrading and install by default?

If you installed 8.04 RC the day before release you got the stable release version on your first update. Depending on what you have installed you may not get any updates. All Ubuntu releases freeze the repositories once they are released and you will only receive security and critical updates. If you really want to check and be sure you can always. 

```
sudo apt-get update
sudo apt-get upgrade
```

---

