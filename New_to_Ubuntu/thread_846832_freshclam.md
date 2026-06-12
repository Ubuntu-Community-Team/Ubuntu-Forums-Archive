---
title: "freshclam"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by poordamnedfool on 2008-07-01
I had an older version of clamav installed i followed this wiki [http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html](http://volatile-minds.blogspot.com/2008/06/installing-clamav-latest-from-source.html) and when I tried to run freshclam I get this error message.

```
WARNING: You must specify at least one database mirror.
```

this install did not place anything into the /usr/bin directory also my freshclam.conf is located in /etc/clamav directory.  here is a copy of what the freshclam.conf reads.

```
# Automatically created by the clamav-freshclam postinst
# Comments will get lost when you reconfigure the clamav-freshclam package

DatabaseOwner clamav
UpdateLogFile /var/log/clamav/freshclam.log
LogVerbose false
LogSyslog false
LogFacility LOG_LOCAL6
LogFileMaxSize 0
LogTime no
Foreground false
Debug false
MaxAttempts 5
DatabaseDirectory /var/lib/clamav/
DNSDatabaseInfo current.cvd.clamav.net
AllowSupplementaryGroups false
PidFile /var/run/clamav/freshclam.pid
ConnectTimeout 30
ReceiveTimeout 30
ScriptedUpdates yes
NotifyClamd /etc/clamav/clamd.conf
DatabaseMirror db.local.clamav.net
DatabaseMirror database.clamav.net
DatabaseMirror db.us.clamav.net

```

Thanks for the help

---

### Post by ChameleonDave on 2008-07-01
Well, you've clearly got database mirrors in your config file, so that looks like a bug in clamav.  Consider reporting it to them.

Meanwhile, just use clamav from the official Ubuntu repositories.

---

### Post by poordamnedfool on 2008-07-01
Ok thanks for the help.

---

### Post by tjwoosta on 2008-07-01
clamav is available from the repository (its not the latest stable version but it works just as well)

ive never had any problems with it

---

