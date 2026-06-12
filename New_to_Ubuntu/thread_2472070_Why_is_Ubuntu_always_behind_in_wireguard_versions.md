---
title: "Why is Ubuntu always behind in wireguard versions?"
date: 2022-02-16
forum: New to Ubuntu
---

### Post by ochompsky3 on 2022-02-16
As long as i've been using wireguard, Ubuntu has consistently remained behind far longer than other distros.  

[https://www.wireguard.com/install/](https://www.wireguard.com/install/)

---

### Post by The Cog on 2022-02-16
You do know that once a version of Ubuntu is released, they don't upgrade the packages in it other than to backport security patches, don't you?
What version of Ubuntu are you looking at?

---

### Post by ochompsky3 on 2022-02-17
> **The Cog said:**
> You do know that once a version of Ubuntu is released, they don't upgrade the packages in it other than to backport security patches, don't you?
What version of Ubuntu are you looking at?

ubuntu server 21.10

---

### Post by The Cog on 2022-02-17
It looks as though the latest wireguard was released in mid-September, only just before Ubuntu 21.10 was released in October. It was probably just after the Ubuntu version freeze prior to their release. Unfortunate timing. I guess the next Ubuntu release (April) will incorporate the latest wireguard.
Here are the various release stages for Ubuntu 21.10: [https://discourse.ubuntu.com/t/impish-indri-release-schedule/18540](https://discourse.ubuntu.com/t/impish-indri-release-schedule/18540)

Strangely, I can't find any release notes that say what the differences are between versions.

---

### Post by ActionParsnip on 2022-02-18
Ubuntu is not a rolling release distribution so packages don't get updated to the latest versions very often

---

### Post by MAFoElffen on 2022-02-18
...Except in the Snap Store, which Server Edition is now included with Snaps. (not by our choice or request.)

---

