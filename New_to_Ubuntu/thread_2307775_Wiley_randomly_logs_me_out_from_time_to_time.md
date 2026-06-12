---
title: "Wiley randomly logs me out from time to time"
date: 2015-12-28
forum: New to Ubuntu
---

### Post by blade4 on 2015-12-28
Hi all, 

So this basically started happening when I installed JWM by apt-get . I've had three of these since and I haven't been able to find any cause for it ( removing jwm didn't help ). I looked at the log file in the var folder ( syslog.1) and found this entry at the time of one of said logouts : 

```
 systemd[1]: Stopping User Manager for UID 119... 
```

I checked this and it seems UID 119 is for the guest session. But I don't know how to proceed from here. 

Thoughts ?

---

### Post by DuckHook on 2015-12-29
...hmmm.

It's not surprising that installing another window manager might jumble some things up. After all, one of the jobs of JWM is to handle logins and this may create a conflict with your old DE. That's why some of us old-timers counsel against multi-DEs on the same install, although, to be fair, it seems that many users run multi-DEs  with no problems. What DE were you running before installing JWM?

You may want to try reinstalling your old DE. After backing up all of your data, of course.

If you want to try JWM with the least likelihood of problems, try installing it over a pure CLI environment like the mini.iso or Ubuntu server.

---

### Post by yetimon_64 on 2015-12-29
> **DuckHook said:**
> ...hmmm.

It's not surprising that installing another window manager might jumble some things up. After all, one of the jobs of JWM is to handle logins and this may create a conflict with your old DE. That's why some of us old-timers counsel against multi-DEs on the same install, although, to be fair, it seems that many users run multi-DEs  with no problems. What DE were you running before installing JWM?

You may want to try reinstalling your old DE. After backing up all of your data, of course.

If you want to try JWM with the least likelihood of problems, try installing it over a pure CLI environment like the mini.iso or Ubuntu server.

+1. Yes, I'm one user who for many years enjoyed multiple DE's with no problems up until I tried to run e17 with unity and lost the lot in a total mess up. This sounds like very good advice (a minimal or server install with other DEs for testing) to me OP. Cheers, yeti.

---

### Post by blade4 on 2016-01-04
Thanks for the replies guys. I think the problem just solved itself after an ubuntu base update . I'll mark this thread as solved for the time being.

---

