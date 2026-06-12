---
title: "Need a system data logger whose file will survive crash?"
date: 2020-01-05
forum: New to Ubuntu
---

### Post by jellicus on 2020-01-05
I'm having a problem with a virgin install that keeps inexplicably locking up. It's a dual boot with win10, which is stable. It's possible something is causing an overheat on my fanless homebuild, but without data I don't know what's going on! Is there an app that will write a CSV or such with logs of the CPU activity and core temps so when it crashes I can graph it and see what if anything was going on there? Obviously, the file needs to be able to survive the crash. I don't know much about these things. Any pointer would be appreciated.

---

### Post by mastablasta on 2020-01-06
psensor or the CLI service sensors would be a place to start

---

### Post by jellicus on 2020-01-06
> **mastablasta said:**
> psensor or the CLI service sensors would be a place to start
I have psensor but I have not seen a file creation tool on it, just the live graph.

---

### Post by TheFu on 2020-01-06
Thermal warnings show up in syslog. But any modern CPU will throttle back rather than fail.

Windows has a long history of ignoring HW issues/failures and continuing.  Best to check all the system log files on Linux.
Depending on the default settings for your system, the boot logs might be overwritten at each boot. You can change this in the journal.conf file.  I keep 1MB of logs. That has always been 3+ boots.

You can also use the built-in remote logging that systemd provides.  That's beyond my knowledge but lots of places use it rather than using rsyslog.

---

### Post by mastablasta on 2020-01-07
logs are found in /var/log

logviewer by default displays only current ones. the old ones are in the directory above and usually have .old ending next to them.

---

