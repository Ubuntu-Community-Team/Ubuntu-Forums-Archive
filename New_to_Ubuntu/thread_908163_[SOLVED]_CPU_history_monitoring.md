---
title: "[SOLVED] CPU history monitoring"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by tjajab on 2008-09-02
Hello, I would like to know of any good tools with which you could monitor the CPU history (i.e. not only the present value) on an Ubuntu server. A web interface would be great, but a command-based utility would work to. I would prefer a simple application which is easy-to-install, rather than a full system monitoring tool which may be complicated to get up and running. Any ideas?

---

### Post by Thingymebob on 2008-09-04
You could create a small shell script that contains 
```

#!/bin/bash
cat date >> /var/log/load.log
cat /proc/loadavg >> /var/logs/load.log

```

/proc/loadavg contains averages for the last 1,5 and 15 minutes

make it executable and schedule it to run however often you want with crontab -e

---

### Post by tjajab on 2008-09-04
Thanks, that is of course a simple and nice solution. I was looking for a nice web interface but this works just as well as for now.

For other users using this: you cannot do "cat date", you have to write just date as date is not a file but a command, but apart from that the script above works fine.

I won't marked this thread as solved, yet, as I would happily hear of web interface solutions to, but thanks so far for the effort.

---

### Post by Thingymebob on 2008-09-04
> **tjajab said:**
> 
For other users using this: you cannot do "cat date", you have to write just date as date is not a file but a command, but apart from that the script above works fine.

Quite right, Apologies

---

### Post by Thingymebob on 2008-09-04
Is this the sort of thing your looking for [http://munin.projects.linpro.no/]("http://munin.projects.linpro.no/") Theres some live examples you can view from this site and a good guide to setting up on debian sarge here [http://www.howtoforge.com/server_monitoring_monit_munin]("http://www.howtoforge.com/server_monitoring_monit_munin")  I would imagine this would work on Ubuntu too

---

### Post by tjajab on 2008-09-04
Thank you! Seems like the exact thing I was looking for.

---

