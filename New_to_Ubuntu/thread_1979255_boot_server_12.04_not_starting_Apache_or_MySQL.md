---
title: "boot server 12.04 not starting Apache or MySQL"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by AndyCanfield on 2012-05-13
Yesterday we installed Ubuntu 12.04 Server. Now it has stopped running MySQL or Apache at boot time. Still runs OpenSSH and Samba. Commands "start mysql" and "/etc/init.d/apache2 start" work fine from an SSH login. It smells as if it is not the daemons who fail, but init simply does not try to launch the daemons. How to get them to start up at boot time?

---

### Post by AndyCanfield on 2012-05-13
I have a lead. When execute the command "runlevel" the answer is "unknown". If I execute the command "telinit 2" then all the daemons are started. I suppose that "telinit 3" would be more proper, to include networking. But I have no idea what runlevel it is booting into, where that is stored on the disk, or even to what extent the new-model "init" program does runlevels. How can I tell what my "default runlevel" is, and how is it configured?

---

### Post by AndyCanfield on 2012-05-13
Weirder and weirder. I created files /etc/init/runlevel#.conf where # is 0 through 9. Each is only started at the given runlevel. Each creates a file named /tmp/runlevel giving the number that run. If I 'telinit 5' then the contents of /tmp/runlevel is "5"; if I telinit 3 the contents of /tmp/runlevel is "3". On my notebook computer, after I boot, the contents of /tmp/runlevel is "2".

But on the server, after I boot, there is no /tmp/runlevel at all! For some reason the init program is not running /sbin/start on the /etc/init/*.conf files! Why not?

---

### Post by AndyCanfield on 2012-05-14
More insanity. I have a file /etc/init/runlevel.conf which reads:
```
# runlevel - record system runlevel
#
# This task is run on startup

description     "log system runlevel"

start on startup

task
script
        /sbin/runlevel >/tmp/runlevel.out
end script
```When I boot, /tmp/runlevel.out DOES NOT EXIST. Why not?

---

### Post by AndyCanfield on 2012-05-16
For those who are trapped in the same problem I have, I invented a kludge fix. The file is named /etc/init/Andy.conf and it reads:
```
# Andy.conf - force boot into runlevel 3
# This task is run when the system starts
description     "force boot into runlevel 3"
start on started ssh
task
script
        if ( ! ps -C mysqld ) ; then /sbin/telinit 3 ; fi
end script
```When init has started the ssh daemon the startup process is almost complete, and so is ready for me to make adjustment. The 'telinit' simply changes the runlevel to what it should have been originally, namely 3 (traditionally the run level of no windowing system but everything else including networking). It appears to work; if I find a bug in it I will post again here.

I still hope that someone out there can tell me how to get init to fire up in runlevel 3 originally. But a kludge fix is better than no solution at all.

---

### Post by paultrotter88 on 2012-07-26
Thanks for posting this! I've got a cloud server that came with 12.04 installed, but the runlevel always came back as 'unknown'. I used your kludge fix to ensure that my server always started up in runlevel 3 with the services I needed. Like you said--it's better than no fix at all...

---

