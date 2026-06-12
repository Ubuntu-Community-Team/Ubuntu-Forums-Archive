---
title: "multiple dbus errors"
date: 2014-03-30
forum: New to Ubuntu
---

### Post by debroos on 2014-03-30
I've just installed a dual boot v12.04 on an XP machine.  It has worked fine until a recent freeze during a software download from Ubuntu, so I forced a reboot.  Ubuntu still seems to work ok, but there are umpteen messages in the Ksystem authentication log - one of which is below.  The messages all refer to the 'dbus' process and start with 'rejected send message...', the only difference between them is in the various numbers .."uid=.." and so on. Any advice on how to deal with this would be very much appreciated 

[system] Rejected send message, 2 matched rules; type="method_call", sender=":1.68" (uid=1000 pid=2090 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.18" (uid=0 pid=1309 comm="/usr/sbin/console-kit-daemon --no-daemon ")

---

