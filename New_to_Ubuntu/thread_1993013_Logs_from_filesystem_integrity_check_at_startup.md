---
title: "Logs from filesystem integrity check at startup"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by Jmob on 2012-06-01
So, ubuntu just did a filesystem integrity check at boot (restarted after the / partition went to 0 bytes from some as-yet unidentified issue, see here [http://ubuntuforums.org/showthread.php?t=1991168](http://ubuntuforums.org/showthread.php?t=1991168)), and I'd like to grab the logs from that, see if it's useful to figure out what happened.  

Are logs of such events stored, and if so, where?

---

### Post by 2F4U on 2012-06-01
There should be a log file in /var/log/fsck.

---

### Post by Jmob on 2012-06-02
Thanks.  The folder has checkfs and checkroot both of which have "(nothing has been logged yet)" as their sole content.  Is this an indication that the check did run but nothing was found, or am I missing something?

---

