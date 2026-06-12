---
title: "cron.daily not running on laptop in 13.04 (anacron)"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by DetroitDoc on 2013-05-16
I have a laptop with 13.04 on it.   I have noticed that the scripts in cron.daily are not being run.  Since it's a laptop, it's not up all the time.  From what I can tell, anacron runs at boot time and should be running all the scripts in cron.daily (if they haven't run yet today).

When I boot my laptop I see the following logs in syslog.  However if I immediately check the process table anacron is no longer running.  So it's mysteriously dying.

```

May 16 10:06:38 todd-Aspire-5750 anacron[1066]: Anacron 2.3 started on 2013-05-16
May 16 10:06:38 todd-Aspire-5750 anacron[1066]: Will run job `cron.daily' in 5 min.
May 16 10:06:38 todd-Aspire-5750 anacron[1066]: Jobs will be executed sequentially

```


If I run anacron (as root) from the command line, everything appears to work correctly.
```

May 14 21:23:17 todd-Aspire-5750 anacron[4400]: Anacron 2.3 started on 2013-05-14
May 14 21:23:17 todd-Aspire-5750 anacron[4400]: Will run job `cron.daily' in 5 min.
May 14 21:23:17 todd-Aspire-5750 anacron[4400]: Jobs will be executed sequentially
May 14 21:28:17 todd-Aspire-5750 anacron[4400]: Job `cron.daily' started
May 14 21:28:17 todd-Aspire-5750 anacron[4543]: Updated timestamp for job `cron.daily' to 2013-05-14
May 14 21:55:18 todd-Aspire-5750 anacron[4400]: Job `cron.daily' terminated
May 14 21:55:18 todd-Aspire-5750 anacron[4400]: Normal exit (1 job run)

```

Can someone with 13.04 check their logs (/var/logs/syslog) for anacron and see if it's actually running cron.daily after a boot?  I'd would be preferable for someone to check a system that doesn't run 24/7 as anacron is re-run out from cron each morning which is a different mechanism.

Thanks!
Doc

---

### Post by DetroitDoc on 2013-05-16
I finally figured it out!   This has been driving me nuts for a few weeks now.   Out of pure luck I happened to catch this after a boot...

```

root      1502  1477  0 10:51 ?        00:00:00 /bin/sh /usr/lib/pm-utils/power.d/anacron true
root      1507  1502  0 10:51 ?        00:00:00 stop -q anacron

```
It looks like the upower package stops certain services when AC power is not present.   This is what was killing off anacron.   It will also re-start the service when AC is restored.  This is extremely cool but I just wish upower would have logged something to make it clearer what was going on.  Upower owes me a week of my time back!  ;)

For those interested here is the /usr/lib/pm-utils/power.d/anacron file.  In theory if you wanted anacron to run on batter power you could remove or alter this script.  I actually kind of wish there was more granularity to control which jobs anacron runs when AC is present or not.   I imagine log rolling would be fine on battery but apt updates, SSD triming, etc you'd prefer to do on AC.

```

#!/bin/sh

# This script makes anacron jobs start/stop when a machine gets or loses AC
# power.

case $1 in
    false)
    start -q anacron || :
    ;;
    true)
    stop -q anacron || :
    ;;
esac


```

---

