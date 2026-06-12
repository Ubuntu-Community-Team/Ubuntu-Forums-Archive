---
title: "AutoStarting Apache Tomcat 7"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by nate10 on 2014-04-25
I am attempting, futally, to get tomcat 7 to autostart on boot. I've read several guides online as to methods to accomplish this. In the end I restart and after everything is loaded I can not access localhost:8080. I will include what I know might help as I am in the complete beginners section I am not entirely sure what all to include.

tomcat7 file in /etc/init.d/
```

# Tomcat auto-start
#
# description: Auto-starts tomcat
# processname: tomcat
# pidfile: /var/run/tomcat.pid

PATH=/sbin:/bin:/usr/sbin:/usr/bin

start() {
 sh /home/office1/GTS/tomcat/bin/startup.sh
}

stop() {
 sh /home/office1/GTS/tomcat/bin/shutdown.sh
}

case $1 in
  start|stop) $1;;
  restart) stop; start;;
  *) echo "Run as $0 <start|stop|restart>"; exit 1;;
esac

```

Process to add tomcat
```

office1@office1:~$ sudo chmod +x /etc/init.d/tomcat7
office1@office1:~$ sudo update-rc.d -f tomcat7 remove
 Removing any system startup links for /etc/init.d/tomcat7 ...
   /etc/rc0.d/K20tomcat7
   /etc/rc1.d/K20tomcat7
   /etc/rc2.d/S20tomcat7
   /etc/rc3.d/S20tomcat7
   /etc/rc4.d/S20tomcat7
   /etc/rc5.d/S20tomcat7
   /etc/rc6.d/K20tomcat7
office1@office1:~$ sudo update-rc.d -f tomcat7 defaults
update-rc.d: warning: /etc/init.d/tomcat7 missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/tomcat7 ...
   /etc/rc0.d/K20tomcat7 -> ../init.d/tomcat7
   /etc/rc1.d/K20tomcat7 -> ../init.d/tomcat7
   /etc/rc6.d/K20tomcat7 -> ../init.d/tomcat7
   /etc/rc2.d/S20tomcat7 -> ../init.d/tomcat7
   /etc/rc3.d/S20tomcat7 -> ../init.d/tomcat7
   /etc/rc4.d/S20tomcat7 -> ../init.d/tomcat7
   /etc/rc5.d/S20tomcat7 -> ../init.d/tomcat7
office1@office1:~$ sudo update-rc.d tomcat7 enable
update-rc.d: warning: /etc/init.d/tomcat7 missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Enabling system startup links for /etc/init.d/tomcat7 ...
 Removing any system startup links for /etc/init.d/tomcat7 ...
   /etc/rc0.d/K20tomcat7
   /etc/rc1.d/K20tomcat7
   /etc/rc2.d/S20tomcat7
   /etc/rc3.d/S20tomcat7
   /etc/rc4.d/S20tomcat7
   /etc/rc5.d/S20tomcat7
   /etc/rc6.d/K20tomcat7
 Adding system startup for /etc/init.d/tomcat7 ...
   /etc/rc0.d/K20tomcat7 -> ../init.d/tomcat7
   /etc/rc1.d/K20tomcat7 -> ../init.d/tomcat7
   /etc/rc6.d/K20tomcat7 -> ../init.d/tomcat7
   /etc/rc2.d/S20tomcat7 -> ../init.d/tomcat7
   /etc/rc3.d/S20tomcat7 -> ../init.d/tomcat7
   /etc/rc4.d/S20tomcat7 -> ../init.d/tomcat7
   /etc/rc5.d/S20tomcat7 -> ../init.d/tomcat7



```

---

### Post by nate10 on 2014-04-28
Ah well in either case if there is anything else I can unclude please be sure to let me know and I will include it.

---

### Post by Danger_Monkey on 2014-04-28
Your script itself looks fine.  You aren't doing a lot of checking, which is OK, but be prepared to add code as needed, to, say, make sure the process isn't already running.  I would include the LSB portion at the top, something like 

```

### BEGIN INIT INFO
# Provides:           tomcat
# Required-Start:     $network $remote_fs $syslog
# Required-Stop:      $network $remote_fs $syslog
# Default-Start:      2 3 4 5
# Default-Stop:       0 1 6
# Short-Description:  Tomcat 
# Description:        Tomcat Web Service
### END INIT INFO

```

---

### Post by nate10 on 2014-04-28
Eh still no luck. I copy and pasted the init to the top of the tomcat7 file but once I restarted the computer and logged in I attempted to load 127.0.0.1:8080 and it was an error screen. Is there a log I can view so I can verify it is attempting to load or see if it's popping errors attempting to load?

---

