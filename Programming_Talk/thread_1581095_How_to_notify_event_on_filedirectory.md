---
title: "How to notify event on file/directory"
date: 2010-09-24
forum: Programming Talk
---

### Post by tranminh on 2010-09-24
Hi,
Is there any body tell me how to record all events occur when an action is taken on given file/directory (get all information such as who/when/what/how open/modifile/delete/move/rename/create an given file/directory)

Thank

---

### Post by pdk on 2010-09-24
you can tell when the file was  modified or accessed using find. nothing else to my knowledge

---

### Post by diesch on 2010-09-24
Maybe incron is what you want.

```

Description: cron-like daemon which handles filesystem events
 incron is an "inotify cron" system. It works like the regular cron but is
 driven by filesystem events instead of time events. This package provides two
 programs, a daemon called "incrond" (analogous to crond) and a table
 manipulator "incrontab" (like "crontab").
 .
 incron uses the Linux Kernel inotify syscalls.
 .
 like cron, each user can edit its own incron tables.
 .
 incron can be used to :
  - notifying programs (e.g. server daemons) about changes in configuration
  - guarding changes in critical files (with their eventual recovery)
  - file usage monitoring, statistics
  - automatic on-crash cleanup
  - automatic on-change backup or versioning
  - new mail notification (for maildir)
  - server upload notification
  - installation management (outside packaging systems)
  - ... and many others
Homepage: http://inotify.aiken.cz/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```

---

