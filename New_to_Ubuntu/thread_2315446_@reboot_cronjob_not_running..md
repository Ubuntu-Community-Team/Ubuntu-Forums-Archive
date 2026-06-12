---
title: "@reboot cronjob not running."
date: 2016-02-28
forum: New to Ubuntu
---

### Post by Supply_Man on 2016-02-28
I have this user cronjob that is supposed to run on reboot and start a gmod server. However, it never actually seems to run. Executing the script manually works just fine. I am relatively new to linux in general, and I am unsure if I am doing something wrong, or if something is broken. 

Cron job:
```
@reboot /home/steam/servers/start_build.sh
```

Cron log:
```

Feb 28 21:33:08 test-server cron[762]: (CRON) INFO (pidfile fd = 3)
Feb 28 21:33:08 test-server cron[798]: (CRON) STARTUP (fork ok)
Feb 28 21:33:08 test-server cron[798]: (CRON) INFO (Running @reboot jobs)
Feb 28 21:33:09 test-server CRON[932]: (steam) CMD (/home/steam/servers/start_build.sh)
Feb 28 21:33:09 test-server CRON[855]: (CRON) info (No MTA installed, discarding output)

```

I am running Ubuntu Server 14.04.4 LTS

It is a user cronjob for a non sudo enabled user.

Any ideas?

---

### Post by jim_deadlock on 2016-02-29
If the script is using any environment variables then you need to be aware that a cron session has very limited environment variables compared to a normal user session.

UPDATE: you can log the output which might give you some clues:

```
@reboot /home/steam/servers/start_build.sh > /home/steam/servers/start_build.log 2>&1
```

---

### Post by ian-weisser on 2016-02-29
Steam should not be started at reboot (the time between poweron and login)

Steam should be started after login, using your ~/config/autostart directory.

---

### Post by Supply_Man on 2016-02-29
> **ian-weisser said:**
> Steam should not be started at reboot (the time between poweron and login)

Steam should be started after login, using your ~/config/autostart directory.

I don't think this will solve the issue. I am trying to get a server to start on reboot, not the steam client. Thanks though.

> **jim_deadlock said:**
> If the script is using any environment variables then you need to be aware that a cron session has very limited environment variables compared to a normal user session.

UPDATE: you can log the output which might give you some clues:

```
@reboot /home/steam/servers/start_build.sh > /home/steam/servers/start_build.log 2>&1
```

I found the problem! I was just doing something dumb with environment variables in the script to get the path it was running from. I just replaced that with the actual path the file is in and it works now! 

I gotta keep the ability to pipe the output into another file in mind.

Thanks for the help.

---

