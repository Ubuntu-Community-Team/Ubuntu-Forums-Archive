---
title: "How do I fix garbled system logs Ubuntu 20.04"
date: 2023-03-10
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-10
Hi, 
For some reason my system logs on OS Ubuntu 20.04 are all messed up. I don't get system logs itemized by login session anymore. Instead, there is one huge log all garbled up, bearing the date Jan 10 2022-March 13 2032.

Is there an easy fix for this glitch, using the command line and bash? 

Thanks for your help.

---

### Post by TheFu on 2023-03-10
Does **journalctl -xe** work?

---

### Post by bhubunt on 2023-03-11
Hi TheFu,
I can't check anymore if the journalctl works as a bios update in process on this Lenovo T460 just was interrupted and the bios, plus laptop is bricked, it seems. When I press the power button, the green light is on for 2 seconds, then the laptop goes dead.

Can this be fixed by inserting a recovery usb or does the whole thing need to be taken apart?

---

### Post by titaniuman on 2023-03-11
Try to check logrotate configuration. Logrotate is a utility that manages log files and rotates them periodically. Check if the logrotate configuration for system logs is correct. You can do this by looking at the /etc/logrotate.d/rsyslog file. Make sure that it is configured to rotate system logs daily or weekly.

---

### Post by TheFu on 2023-03-11
> **titaniuman said:**
> Try to check logrotate configuration. Logrotate is a utility that manages log files and rotates them periodically. Check if the logrotate configuration for system logs is correct. You can do this by looking at the /etc/logrotate.d/rsyslog file. Make sure that it is configured to rotate system logs daily or weekly.

For the last 20+ yrs, I've not seen a default system install have any logrotate issues. I suppose it could happen, but the only times I've seen it is when someone created their own network dæmon with startup/status/stop controls (or a systemd unit file) and forgot to clean their own log files.

Systemd (as controlled by journalctl) is where all system logs are stored.  The text that gets outputted for dmesg and syslog come from the systemd journal.  Now, that journal is controlled by /etc/systemd/journald.conf which has settings to control max sizes and forced deletions.  I have a short cheatsheet of commands:
```
  journalctl -xe            # See errors for last service, with eXtra information
  journalctl -b             # See current boot logs
  journalctl -b -1          # See prior boot log
  journalctl -b -3          # See 3 boot logs ago
  sudo journalctl -k        # See current kernel logs
  journalctl --since=today
  journalctl -S today       # See logs for today, from midnight, yesterday/tomorrow
  journalctl -xe -S today   # See errors for today, from midnight today
  sudo journalctl -S -1h    # See logs for last 1 hour m/w == minutes/weeks
  sudo journalctl _PID=751  # find logs for a specific PID
  sudo journalctl _UID=1000 # find logs for a specific user
  sudo journalctl /usr/bin/anacron # logs for a specific executable
  journalctl -u nfs-kernel-server.service
  journalctl -u nfs-server.service -S -2h
  journalctl -p 0           # emergency
                1           # alert
                2           # critical
                3           # error
                4           # warning
                5           # notice
                6           # info
                7           # debug
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```

Anyway, hope this is helpful to someone.  If /var is full, use the vacuum command ASAP. 200M should be at least 3-7 days of logs, so it is unlikely to remove anything important for a recent issue.

---

### Post by mikodo on 2023-03-11
> **TheFu said:**
> Anyway, hope this is helpful to someone.  If /var is full, use the vacuum command ASAP. 200M should be at least 3-7 days of logs, so it is unlikely to remove anything important for a recent issue. Yes!  Thank you.
  ```
$  journalctl --disk-usage   Archived and active journals take up 2.0G in the file system. $   sudo journalctl --vacuum-size=200M [sudo] password for mikodo:  Deleted archived journal ... lots Vacuuming done, freed 1.8G of archived journals from /var/log/journal/0ebb161eade84c049f78d41f21b79971.
```

---

