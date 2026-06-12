---
title: "[SOLVED] cron issue :("
date: 2008-07-16
forum: New to Ubuntu
---

### Post by FlyerDie on 2008-07-16
Hi,

I try to schedule tasks using cron, but don't works. So to test it, I have the following configuration which runs mc (Midnight Commander). But nothing happens..:confused: Here is the result of crontab -l:

```
01 * * * 1-5 mc
```

Supuse to run avery 01 minute hour, from Monday-Friday... but don't work..Am I missing something?

Regards!

---

### Post by Bachstelze on 2008-07-16
cron cannot run "interactive" commands, like mc, vi, or stuff like that. How would it be supposed to know which terminal to run it on anyway? You must run a non-interactive command, for exemple :

```
01 * * * 1-5 date --rfc-3339=seconds >> ~/crontest
```

---

### Post by fatality_uk on 2008-07-16
I run this type of command to start top in a terminal. I don't have **mc**, but I am guessing it will work just the same.
Edit this line into your cron job

> 01 * * * 1-5 export DISPLAY=:0 && gnome-terminal --command="mc"

---

### Post by FlyerDie on 2008-07-16
thanks both!
fatality_uk you got the point ;) works great!

Regards

Diego

---

### Post by fatality_uk on 2008-07-16
No prob. Glad to help ;)

---

