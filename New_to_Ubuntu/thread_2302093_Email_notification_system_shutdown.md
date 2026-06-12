---
title: "Email notification system shutdown"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by silverspr on 2015-11-07
HI, fairly new to Ubuntu but having good success.  Just upgraded from 15.04 to 15.1 (wily).  
I'm sure this is very simple to solve, I am no longer getting email notifications 10 min prior to a system scheduled shutdown job in Cron i.e. "Shutdown scheduled for Fri 2015-10-30 22:31:01 MDT, use 'shutdown -c' to cancel." The job is scheduled in cron (using sudo).  I've checked config files for ssmtp, cron etc.  it all looks good.  I get email notifications of other jobs, just not this one: 30 22 * * * /sbin/shutdown -h +1
The job does run and the machine shuts down I just don't get the email notification.  this is the same configuration prior to upgrading to wily where it was working.

thanks

---

### Post by silverspr on 2015-11-08
Hi There....
when running the shutdown script from within Webmin, I get this output: [COLOR="#FF0000"]Failed to call ScheduleShutdown in logind, proceeding with immediate shutdown: Message recipient disconnected from message bus without replying?  [/COLOR]
Does that help anyone with what his might mean!? thanks

---

