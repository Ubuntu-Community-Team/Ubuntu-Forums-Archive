---
title: "System Log Problem"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by dunbrokin on 2012-04-04
Nothing is showing up on my log viewer...even when I start it from the command line I just get a blank page...this seems very weird. I wonder if I might be compromised. What am I doing wrong?

gnome-system-log

just gives me a blank sheet!

---

### Post by hughr2005 on 2012-04-04
Have you checked the log files in /var/log?

---

### Post by dunbrokin on 2012-04-04
> **hughr2005 said:**
> Have you checked the log files in /var/log?

I can certainly find Syslog and kernal log there and access them.


Apr  4 19:09:00 pj-E6420 kernel: [282842.790635] type=1400 audit(1333523340.742:313): apparmor="DENIED" operation="open" parent=1 profile="/usr/bin/evince" name="/run/udev/data/b8:5" pid=32649 comm="evince" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Apr  4 19:17:02 pj-E6420 CRON[1326]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  4 19:54:45 pj-E6420 kernel: [285582.772266] logitech 0003:046D:C512.0002: can't reset device, 0000:00:1d.0-1.1.3/input0, status -71
Apr  4 19:54:45 pj-E6420 kernel: [285582.772278] generic-usb 0003:046D:0A12.0001: can't reset device, 0000:00:1d.0-1.1.2/input3, status -71
Apr  4 19:54:45 pj-E6420 kernel: [285582.776266] usb 2-1.1: clear tt 1 (0080) error -71

Does this mean anything...my machine definately went weird around this time last night.

---

### Post by hughr2005 on 2012-04-04
That's mad. I don't know what that is to be honest. The thing is though, the only reason gnome-system-log wouldn't work (as long as the logs are actually there) is if that has been changed in some way itself. Unless I'm a n00b for some reason :P I don't see why input devices and other USB errors would affect the logging system in any way though...

Any logging specialists out there?

---

