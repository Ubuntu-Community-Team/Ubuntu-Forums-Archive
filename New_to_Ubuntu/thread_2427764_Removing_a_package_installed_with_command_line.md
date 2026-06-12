---
title: "Removing a package installed with command line?"
date: 2019-09-25
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-09-25
For Kodi on 16.04 I had to install a few packages from zesty. The machine is working fine of course but I'd like to know how to remove them if necessary. These were downloaded manually and installed via dpkg -i package.deb. They aren't showing up in apt, for obvious reasons. If I was smart I would have put a apt server on my server and installed that way but I didn't.

---

### Post by cruzer001 on 2019-09-25
dpkg --remove package.name then use apt autoremove to clean up
or is it not that simple?
What packages are involved?

---

### Post by Tadaen_Sylvermane on 2019-09-26
I unpacked the deb and got the exact name and did dpkg --get-selections | grep python-crypto and the package came up. Was able to remove with apt. And apparently I never installed the other one. So good to go. TY, solved.

---

### Post by Impavidus on 2019-09-26
> **Tadaen_Sylvermane said:**
> They aren't showing up in apt, for obvious reasons.
Doesn't sound that obvious to me. If it's a .deb package, all interfaces to dpkg package management (dpkg, apt, synaptic, Ubuntu Software, ...) should know about it.

---

### Post by Tadaen_Sylvermane on 2019-09-26
I figured apt only knew about stuff it could scan from repos. Didn't think it would without that.

---

### Post by r_widell on 2019-09-28
BTW- Synaptic will show packages that have been manually installed if you select the "status" submenu in the lower left pane, then "manual or obsolete in the upper left pane. Needless to say, it can uninstall or purge them as well.

ron

---

