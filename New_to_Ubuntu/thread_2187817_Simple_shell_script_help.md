---
title: "Simple shell script help"
date: 2013-11-13
forum: New to Ubuntu
---

### Post by hookitup on 2013-11-13
Hey Folks,

Im trying to write a script to check if a specific service is running and if so run a command. This is what i have so far but cant seem to get it to work. as i think it gets stuck at the read part, my plan is to put this in a cron job

```
ps aux | grep srvtmx1 | awk '{print $15}'
read psstats


if [ $psstats = srvtmx1 ]; then
        echo "blah blah is runign"
else
        exit 0
fi



```

when i run it, it shows me the output of the ps command and stops. i was thinking of adding 
```
ps aux | grep srvtmx1 | awk '{print $15}' > ps.log
```
but i do not know how to tell the script to read from the log. maybe there is a different way. does anybody have any ideas ?

---

### Post by Lars Noodén on 2013-11-14
Don't you mean to capture the output of ps etc into the variable psstats?

```

psstats=$(ps aux | awk '/srvtmx1/ {print $15}').

```
 
If you are just grepping for a process name, you might look at [pgrep](http://manpages.ubuntu.com/manpages/trusty/en/man1/pgrep.1.html) instead.

Also, grep is redundant if you are using awk.  Awk can select with pattern matching (/srvtmx1/) or against a field ($2 == "srvtmx1").

---

### Post by Habitual on 2013-11-14
just another example/solution I came up with for zabbix_agent.
```

#!/bin/bash
### zabbix-agentd pidcheck cron script
### Written by John Jones 
### Date: Mon Apr 30, 2012

SERVICE='zabbix_agentd'
 
if /usr/bin/pgrep $SERVICE > /dev/null
then
    exit 0 
else
    /usr/sbin/zabbix_agentd
    exit 1
fi
#EOF


``` 
Cron:
```
*/1 * * * * /root/zbxcheck.sh
```

 Stopped zabbix_agentd manually and waited 1 minute. It fired.

Obviously, you should decide if root will run this or a user and does that user have the ability to start said "$SERVICE"?

---

