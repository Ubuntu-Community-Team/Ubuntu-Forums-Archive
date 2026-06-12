---
title: "Cron for Root"
date: 2008-10-05
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-05
I have recently setup a server and now would like to have cron ssh my data over there. I set this up but it isn't executing?? and the log is empty

I was opening the crontab for root via these commands (ls -l, just showing the files there)
```
aidan@aidan-desktop:/etc/cron.d$ ls -l
total 8
-rw-r--r-- 1 root root 244 2007-03-04 22:38 anacron
-rw-r--r-- 1 root root   0 2008-09-25 23:00 archive.log
-rwxr-xr-x 1 root root 732 2008-09-24 20:53 archive.sh
aidan@aidan-desktop:/etc/cron.d$ su
Password: 
root@aidan-desktop:/etc/cron.d# crontab -e

```

Heres the crontab
```
# m     h       dom     mon     dow     command
0       23      *       *       0,4     sudo /etc/cron.d/archive.sh >> /etc/cron.d/archive.log

```

and heres /etc/cron.d/archive.sh
```
#!/bin/bash

#EDU
tar jcf - /home/aidan/edu | ssh 192.168.15.101 "cat > /home/aidan/edu`date +%F`.tar.bz2"
ssh root@192.168.15.101 "ls /home/aidan/edu*.tar.bz2 | grep -v \"`ls /home/aidan/edu*.tar.bz2 | tail -2`\" > /tmp/arch.ssh; rm -f `cat arch.ssh`"

#PROGS
tar jcf - /home/aidan/progs | ssh 192.168.15.101 "cat > /home/aidan/progs`date +%F`.tar.bz2"
ssh root@192.168.15.101 "ls /home/aidan/progs*.tar.bz2 | grep -v \"`ls /home/aidan/progs*.tar.bz2 | tail -2`\" > /tmp/arch.ssh; rm -f `cat /tmp/arch.ssh`"

#DATA
tar jcf - /data | ssh 192.168.15.101 "cat > /data/data`date +%F`.tar.bz2"
ssh root@192.168.15.101 "ls /data/data*.tar.bz2 | grep -v \"`ls /data/data*.tar.bz2 | tail -2`\" > /tmp/arch.ssh; rm -f `cat /tmp/arch.ssh`"

```

Thank you

---

### Post by jordilin on 2008-10-05
> **Mr.Macdonald said:**
> I have recently setup a server and now would like to have cron ssh my data over there. I set this up but it isn't executing?? and the log is empty

Heres the crontab
```
# m     h       dom     mon     dow     command
0       23      *       *       0,4     sudo /etc/cron.d/archive.sh >> /etc/cron.d/archive.log

```


Thank you
write 2>&1 at the end, and STDERR will be redirected to archive.log, and probably you will see what's going on. I see [email]root@ipadress...If[/email] server is an Ubuntu, does it have root user enabled? I've never used Ubuntu as server, but in desktop "root" user is disabled and it should be done by sudo.

```

# m     h       dom     mon     dow     command
0       23      *       *       0,4     sudo /etc/cron.d/archive.sh >> /etc/cron.d/archive.log 2>&1

```

---

### Post by geirha on 2008-10-05
Also, using sudo in root's crontab is unnecessary, since it's already being run as root.

And since you try to use ssh without keyboard input, I assume you've set up [host-based authentication]( http://www.ssh.com/support/documentation/online/ssh/adminguide/32/Host-Based_Authentication.html) or similar?

---

### Post by Rich78 on 2008-10-07
I wouldn't recommend having an automated job requiring root permissions to the server it's copying too.

Could you not have a user area?

---

