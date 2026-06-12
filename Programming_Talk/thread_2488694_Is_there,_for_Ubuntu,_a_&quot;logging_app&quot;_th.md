---
title: "Is there, for Ubuntu, a &quot;logging app&quot; that I can call from Perl?"
date: 2023-07-12
forum: Programming Talk
---

### Post by SergioQ on 2023-07-12
Is there, for Ubuntu, a "logging app" that I can call from Perl?

I am writing some Perl scripts, and my knowledge/experience with Ubuntu (and Perl) are very limited.  

Essentially I would like some of my Perl scripts to save/record use and events. Moistly for debugging purposes.  This is something I am already doing by appending to a text file within my server.  However, since the scripts may be called multiple times at once I am unsure of "locking" events and such.

I thought maybe someone might have already created an "debug logging" app, that my perl script can call.

Thank you

---

### Post by The Cog on 2023-07-12
My first thought might be to use logger. For a simple example:
```
logger "Unicorns available at half price today"
tail /var/log/syslog
```
I'm not familiar enough to know how to log to different files though.

---

