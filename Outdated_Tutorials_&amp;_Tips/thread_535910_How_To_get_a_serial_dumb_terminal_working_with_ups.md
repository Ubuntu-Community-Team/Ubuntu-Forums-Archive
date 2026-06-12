---
title: "How To get a serial dumb terminal working with upstart."
date: 2007-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by bigfox on 2007-08-27
I got my Wyse dumb terminal working with Ubuntu 7.04 using upstart.

In the directory /etc/event.d
Create the file ttyS0 containing the fallowing text:


```
# ttyS0 - getty
#
# This service maintains a getty on ttyS0 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
start on stopped ttyS0

stop on shutdown

respawn
exec /sbin/getty 19200 ttyS0 vt100
```

ttyS0 is COM 1
ttyS1 is COM 2
etc..
Change as necessary for your system.

The part "start on stopped ttyS0" restarts the process if it crashes or exits.  I was having trouble getting it to come back up after logging out on the dumb terminal or if a program run on the terminal crashed.  This solves that problem.

---

### Post by jelabarre on 2009-09-22
But now that things have gotten moved around in Karmic, grub has become grub2, etc, what has to change in these instructions?  I have been able to get karmic-server-alpha6 to show me boot messages over the serial connection, but I cannot get Grub2 to show on serial, nor can I log in to a serial terminal once the system has booted.

I'm looking for this as a failover for a headless system, in case of network issues where SSH would not be an option.

---

