---
title: "[SOLVED] very quick apt-get and repository question..."
date: 2008-10-12
forum: New to Ubuntu
---

### Post by earthpigg on 2008-10-12
what happens if i have two repositories in sources.list (or whatever the file is called :) ) that contain different versions of the same package?

will it go with whichever package claims to be the newest...?

does it keep track of where i got package X from, and only upgrade it from there? or will i be asked to upgrade from version 1 of package X (from Ubuntu repository) to version 1.1 of package X (that just showed up on John Doe's repository)...?

---

### Post by hyper_ch on 2008-10-12
it will take the newer one... however you could force it to use the older version.

---

### Post by eternalnewbee on 2008-10-12
Neither am I (an expert) but I think it will upgrade to the newest version..

---

### Post by earthpigg on 2008-10-12
and it will upgrade 'cross-repository', too?

---

### Post by lswest on 2008-10-12
Yes, if the package in a different repository is newer, it will upgrade from that one.

Think of WINE being offered in Ubuntu and then the winehq repo...the winehq one is newer every time, and so the upgrades come from there, no matter which was originally installed.

---

### Post by eternalnewbee on 2008-10-12
I would say yes.
Trial & error... that's how we make progress.

---

