---
title: "(rsyslog)  Unable to get remote syslog"
date: 2014-11-13
forum: Philippine Team
---

### Post by thirdpaa on 2014-11-13
I have rsyslog running on Ubuntu 12.04.5 which collects syslog messages over UDP (514). It suddenly stopped receiving logs from the remote server. 

All other servers connected to rsyslog are able to gather syslogs just fine.

when I issue **[FONT=courier new]fuser -u syslog.log[/FONT]**, it returns nothing. 

What could be the cause of this issue?

thanks,

---

