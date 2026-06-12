---
title: "Cannot add upstart job"
date: 2015-11-20
forum: New to Ubuntu
---

### Post by Nick_Weaver on 2015-11-20
Hi, 

I've been trying to figure this out for hours, and i'm just not sure what to do anymore.   I've been trying to figure out how to just get anything running in upstart, but it always says 'Unknown Job'  pretty much no matter what i do.  I add all my conf files into /etc/init/<name>.conf
I've got one super simple conf (called simple.conf) that is only:
"
description "test"
author "name"

start on runlevel [2345]

stop on runlevel [016]

exec sleep 100000000
"
and that doesn't work.  i've tried init-checkconf -d simple.conf and it says the syntax is ok.  i've tried initctl reload-configuration at least 20 times.  i've rebooted at least 10 times.  i've tried starting on different events from:

start on (started filesystem) and (started networking) 

to 

start on runlevel [5]

i've run initctl check-config and it only says there's an error with unity-panel-service-lockscreen, which has no .conf file that i can find.

i've tried checking initctl list and looking for the new job, it is not there, one time i was able to get them to show up by doing 'ev=UPSTART_SESSION initctl list' but that stopped working.  

Ive upgraded, still not working.  I did the example here : [https://www.digitalocean.com/community/tutorials/the-upstart-event-system-what-it-is-and-how-to-use-it](https://www.digitalocean.com/community/tutorials/the-upstart-event-system-what-it-is-and-how-to-use-it) and it's super simple echo job is still 'Unknown job'.  I've copied the example here: [https://newcome.wordpress.com/2012/02/26/running-programs-as-linux-daemons-using-upstart/](https://newcome.wordpress.com/2012/02/26/running-programs-as-linux-daemons-using-upstart/) and it also 'Unknown job'.  i've done initctl reload-configuration and rebooted on both the example jobs and that did nothing.  I'm at a loss as to what i should be doing...

Running Ubuntu 14.04: 
"$ uname -a"
"Linux 3.19.0-33-generic #38~14.04.1-ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux"

upstart version: 
"initctl --version:"
"initctl (upstart 1.12.1)"

---

### Post by v3.xx on 2015-11-20
Your not using systemd?

[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

---

### Post by Nick_Weaver on 2015-11-20
well, that wiki page says that systemd isn't the standard init until 15.04.  I'm running 14.04.  I also ran the check they listed to tell which init i'm using: 
$ps -p1 | grep systemd && echo systemd || echo upstart
upstart

I'm pretty sure i'm running upstart.

---

