---
title: "&quot;Partial upgrade&quot;...what is it?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by werty2010 on 2011-09-27
the update manager for the first time offered me a "partial upgrade".
what is it and why this is happening?

---

### Post by ninjaaron on 2011-09-27
Don't do it. Wait for a few hours or a day and try to update again.  It can mean that repositories are in the process of being updated when you tried.  You normally only get this message if you are running the development version of Ubuntu, or perhaps depending on the PPA's you may have added.

Running a partial upgrade can break stuff.

---

### Post by seawolf167 on 2011-09-27
Take a look at the info posted [here ]("http://www.ubunturoot.com/2009/12/ubuntu-1004-update-manager-offers.html")- it is for an older version, but still applies to new[er] versions. Long story short, I highly suggest not upgrading until you have a full upgrade available.

---

### Post by stmiller on 2011-09-27
Partial upgrade means additional updates are still in the works.

If it is not critical, just wait a day or so until all updated packages are ready.

---

### Post by werty2010 on 2011-09-27
o oh... i did the "partial" upgrade(forgot to check the email..) and although my system is still stable, i lost some functionality like the banshee extension for lyrics. also i have the feeling that it didnt download all the updates without giving me any other available when i did a recheck.
is there any way to check this?

---

### Post by seawolf167 on 2011-09-27
You can try

```
sudo apt-get update && sudo apt-get upgrade
```

other than that, you basically have to wait until they are released

---

