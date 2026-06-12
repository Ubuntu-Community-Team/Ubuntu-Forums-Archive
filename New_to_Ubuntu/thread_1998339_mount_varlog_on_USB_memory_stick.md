---
title: "mount /var/log on USB memory stick"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by lseg on 2012-06-06
Hi all,

I am trying to setup an home server, and used 3 WD green Hard disks for it.
Apparently they have some issues with the fact that linux is always updating its logs (they quickly go into idle).
[http://wdc.custhelp.com/app/answers/detail/a_id/5357/session/L3RpbWUvMTMzMTMwMTI1OS9zaWQvbzdOemNGU2s%3D](http://wdc.custhelp.com/app/answers/detail/a_id/5357/session/L3RpbWUvMTMzMTMwMTI1OS9zaWQvbzdOemNGU2s%3D)

Would it be possible to move the location of these logs (var/logs) to a USB memory stick instead. This way the HD could remain idle most of the time.

Should I move more than /var/logs only ?

Kind regards,

Luc

---

### Post by matt_symes on 2012-06-09
Hi

You can mount /var/log on a pen stick if you want but is probably not good for the pen drive in the long run.

There is another suggestion though.

Mount /var/log as a tmpfs (in memory filing system) and copy the files created in it to the disc once a day on a cron job (or at a frequency that is comfortable for you) or when the computer is rebooted.

You may have to create the existing directory structure under /var/log for this to work, using a script.

Be aware that if the server crashes or is compromised you may lose the ability to trace and track what happened.

Kind regards

---

