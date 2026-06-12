---
title: "[SOLVED] Killing a process with unknown PID"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by t0p on 2008-05-25
Most days - but not every day - I run *wvdial* on my computer.  I may start and stop it several times in a day.  Some days I don't run it at all.

I want the computer to automatically kill *wvdial* at midnight every night, if it's running.  How could I set this up?

---

### Post by Monicker on 2008-05-25
You could set up a cron job which runs the following:
```

pkill -f wvdial
```

---

### Post by t0p on 2008-05-25
> **Monicker said:**
> You could set up a cron job which runs the following:
```

pkill -f wvdial
```

**pkill** huh?  I didn't know that one.  Thanks!!

---

