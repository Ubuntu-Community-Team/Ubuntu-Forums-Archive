---
title: "[SOLVED] Help with Screenlets"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by lisab34 on 2008-10-03
Ok I know how to work the Screenlets, BUT how do I keep them on my screen when I log off. When I log back on my screen they are gone and I have to launch them again.... PLEASE HELP...Im new to Linux/Ubuntu and Im going nuts here.  LisaB:(

---

### Post by binbash on 2008-10-03
At screenlet manager select the screenlet you want to keep and tick "auto start on login"

---

### Post by ddarsow on 2008-10-03
> **lisab34 said:**
> Ok I know how to work the Screenlets, BUT how do I keep them on my screen when I log off. When I log back on my screen they are gone and I have to launch them again.... PLEASE HELP...Im new to Linux/Ubuntu and Im going nuts here.  LisaB:(

There is an "autostart on login" option for each one. Simply check that and for the ones you want to start. You will also have to meke sure that the Screenlets applet is included in the session manager on the startup tab.

If not there, you need this command for a new startup:
/usr/share/screenlets-manager/screenlets-daemon.py

---

### Post by lisab34 on 2008-10-03
THANK YOU all sooo much!!! They are all stayin put now...:D

---

