---
title: "no log when clamd restart in rsyslog"
date: 2015-08-14
forum: New to Ubuntu
---

### Post by zerop2 on 2015-08-14
/etc/init.d/rsyslog restart
/etc/init.d/clamav-daemon restart

already edited the following conf

/etc/clamav/clamd.conf
LogFacility local6

 /etc/rsyslog.d/50-default.conf
local6.*                        /var/log/syslog

---

