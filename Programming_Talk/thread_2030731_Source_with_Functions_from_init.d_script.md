---
title: "Source with Functions from init.d script"
date: 2012-07-21
forum: Programming Talk
---

### Post by gwcurran on 2012-07-21
I have created a file with a number of bash functions defined. When I "source" it from another bash script that I execute while logged on, everythinng runs as expected. However, if I attempt to source it in a script that is linked as part of my startup (say from /etc/rc2.d/S99test) the attempt to source fails.
 
For example, if my functions file, "test_functions", contains:
 
```
 
#!/bin/bash
 
function test ()
{
        echo "Test function output..." >> /tmp/test.out
}

```
 
And I source in an init script, "/etc/init.d/test_init.sh":
 
```
 
#!/bin/sh
 
### BEGIN INIT INFO
# Provides:
# Required-Start:    $remote_fs $syslog $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Run /etc/rc.local if it exist
### END INIT INFO
 
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:
 
. /lib/init/vars.sh
. /lib/lsb/init-functions
. /usr/local/repo/test_functions
 
do_start() {
.
.
.

```
 
If I execute the script while logged in everything is fine. But when the system is rebooted, the attempt to source fails. The error that I managed to trap is as follows:
 
```
 
/usr/local/repo/test: 3: Syntax error: "(" unexpected

```
 
I also noticed that when I am logaged on I can use the command "source" in the script but during reboot a "command not found error" occurs leading me to believe that there is some inherit difference in the execution environment.
 
How can I workaround this issue?

---

### Post by spjackson on 2012-07-21
> 
```

#!/bin/sh

### BEGIN INIT INFO

```This is a sh script, not a bash script. You cannot source bash functions in sh because sh does not support that syntax.

---

### Post by gwcurran on 2012-07-21
:confused:
 
Exhaustion has finally taken its toll. Thank you and apologies for not spotting that.

---

