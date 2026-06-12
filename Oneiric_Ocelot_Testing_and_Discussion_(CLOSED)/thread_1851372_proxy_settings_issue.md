---
title: "proxy settings issue"
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by andiqo on 2011-09-28
I experience issues with oneiric for proxy settings. I have read bug#795519, but for me I still have the problem with Firefox and Eclipse.

What I have done:
 - configure my proxy via GUI and press "Apply system wide"
 - check that it is OK in /etc/environment
 - check that "gsetting gsettings list-recursively org.gnome.system.proxy" provides good results

When I launch Chromium which use native settings, no problem to access the Internet.
When I launch FF with "Use system settings proxy" enabled, i cannot access the Internet.
When I launch Eclipse IDE and try to "Check for updates" (with native proxy settings), it does not work


Anyone else experiencing the same issue?
Thanks a lot for your help.
++andiqo

---

