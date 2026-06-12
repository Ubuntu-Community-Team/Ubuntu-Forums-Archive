---
title: "[SOLVED] syslog --MARK--"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-07
In the syslog, what does --MARK-- mean?

---

### Post by ChameleonDave on 2008-07-07
> **dunbrokin said:**
> In the syslog, what does --MARK-- mean?

That question really confused me!

I did a search, and found a file at /var/log/syslog.  Is that the one you mean?  In it, the very last entry was "Jul  7 14:53:08 Chameleon -- MARK --".

I would think that it marked the end of the file, but if I add a new device to the system, another entry appears below the "-- MARK --" entry.

The weird thing is, that entry seems to have been added at the moment that I searched for it.  :confused:

---

### Post by dunbrokin on 2008-07-07
> **ChameleonDave said:**
> That question really confused me!

I did a search, and found a file at /var/log/syslog.  Is that the one you mean?  In it, the very last entry was "Jul  7 14:53:08 Chameleon -- MARK --".

I would think that it marked the end of the file, but if I add a new device to the system, another entry appears below the "-- MARK --" entry.

The weird thing is, that entry seems to have been added at the moment that I searched for it.  :confused:


Yup, that is the one I mean...

---

### Post by tino27 on 2008-07-07
The --MARK-- messages are added at regular intervals just to indicate that syslogd is still working, even when no other messages are added.

---

### Post by dunbrokin on 2008-07-07
> **tino27 said:**
> The --MARK-- messages are added at regular intervals just to indicate that syslogd is still working, even when no other messages are added.

You learn something new every day....thanks for that...

---

### Post by ChameleonDave on 2008-07-08
> **dunbrokin said:**
> You learn something new every day....thanks for that...

Perhaps you could use the "Thread Tools" menu to mark this thread as "SOLVED" for future users.

---

