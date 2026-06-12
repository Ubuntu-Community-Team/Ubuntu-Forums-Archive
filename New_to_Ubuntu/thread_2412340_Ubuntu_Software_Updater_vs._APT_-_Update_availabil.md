---
title: "Ubuntu Software Updater vs. APT - Update availability"
date: 2019-02-11
forum: New to Ubuntu
---

### Post by thenall on 2019-02-11
Hello.

I noticed that sometimes the Ubuntu **Software Updater** scans for updates and concludes *"The software on this computer is up to date"*, whereas "**apt list --upgradable**" will still show packages that can be updated.

And, indeed, in this situation running "**apt upgrade**" will install updates. So it seems that either Software Updater and APT sometimes get "out of sync", or they use a different policy to determine which packages can be updated. Or am I missing something?

I was under the impression that Software Updater pretty much is just a GUI front-end that uses APT infrastructure under the hood... :confused:

Regards.

---

### Post by deadflowr on 2019-02-11
Ubuntu implements something called phased updates in update manager (aka software updater)
See: [https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

---

### Post by thenall on 2019-02-11
> **deadflowr said:**
> Ubuntu implements something called phased updates in update manager (aka software updater)
See: [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Thanks for info.

---

