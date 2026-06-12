---
title: "How to run startup script"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by C00kie88 on 2012-08-09
Hi all,
 
I'm trying to run script below as startup script to allow sawmill program to start automatically.
 
The code as below:

#!/bin/sh
# Startup script for Sawmill
# function library.
. /etc/rc.d/init.d/functions
# See how we were called.
case "$1" in
  start)
 echo -n "Starting sawmill: "
 daemon sawmilld
 echo
 touch /var/lock/subsys/sawmill
 ;;
  stop)
 echo -n "Shutting down sawmill: "
 killproc sawmill
 echo
 rm -f /var/lock/subsys/sawmill
 rm -f /var/run/sawmill.pid
 ;;
  status)
 status sawmill
 ;;
  restart)
 $0 stop
 $0 start
 ;;
  reload)
 echo -n "Reloading sawmill: "
 killproc sawmill -HUP
 echo
 ;;
  *)
 echo "Usage: $0 {start|stop|restart|reload|status}"
 exit 1
esac
exit 0

Does it matter the location of the script?
My understanding is have to put it to /etc/init.d. is It correct? or do i have to use crontab?
Do i need to create symbolic link? I'm so confused..
What is the simple way for me to do it? 
 
I tried to read the manual from [http://www.sawmill.net/cgi-bin/sawmill8/docs/sawmill.cgi?dp+docs.faq.entry+webvars.entry+runatstartup+webvars.username+samples+webvars.password+sawmill](http://www.sawmill.net/cgi-bin/sawmill8/docs/sawmill.cgi?dp+docs.faq.entry+webvars.entry+runatstartup+webvars.username+samples+webvars.password+sawmill) 
and i dont understand at all..
 
Please help

---

### Post by ubudog on 2012-08-09
Hi C00kie88. Put that script in /etc/init.d.  If you want it to run automatically, edit /etc/rc.local and add the following **before** "exit 0":

```
/etc/init.d/sawmill start
```

That should start Sawmill automatically on start-up.  

Best,
ubudog

---

### Post by C00kie88 on 2012-08-09
Hi Ubudog,
 
Ok this is what i did:
 
1. I have copied the script called sawmill.sh to /etc/init.d directory
2. I have edited /etc/rc.local (before exit 0) by adding /etc/init.d/sawmill start
 
It's not starting up :(

---

### Post by josephmills on 2012-08-09
Did you mark the script as executable?

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by C00kie88 on 2012-08-10
Hi Josephmills,
 
i have changed the permission to chmod u+rwx to the script file.
 
Cheers,

---

