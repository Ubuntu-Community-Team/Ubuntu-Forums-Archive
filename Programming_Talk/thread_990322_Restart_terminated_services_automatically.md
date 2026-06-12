---
title: "Restart terminated services automatically"
date: 2008-11-22
forum: Programming Talk
---

### Post by SwedishWings on 2008-11-22
I'm implementing a few service that will run on an embedded system. In other words, they must be restarted if they for any reason would terminate. 

From what i figured so far, they'll be launched from /etc/init.d/* to follow the Linux standard.

What i do not know, is how to automatically restart any service if it would terminate. Is there a simple standard way to do this?

Thanks in advance,
Mike

---

### Post by quux on 2008-11-22
Unfortunately init.d does (at least AFAIK) not support automated restarts of terminated services. If you're not tied to init.d, then you might consider starting your service using *daemontools* ([http://cr.yp.to/daemontools.html](http://cr.yp.to/daemontools.html)) which provides this particular feature.

The FAQ ([http://cr.yp.to/daemontools/faq.html](http://cr.yp.to/daemontools/faq.html)) should give you a quick overview how to use it. An Ubuntu package of the most recent version is available in the universe repository.

---

### Post by SwedishWings on 2008-11-23
Thanks for the pointer. Reading that makes me wonder why not all new services are using it. Very handy indeed.

Regards,
Mike

---

### Post by Greyed on 2008-11-23
There is also monit.  

```

Package: monit
Description: A utility for monitoring and managing daemons or similar programs
 monit is a utility for monitoring and managing daemons or similar
 programs running on a Unix system. It will start specified programs
 if they are not running and restart programs not responding.
 .
 monit supports:
  * Daemon mode - poll programs at a specified interval
  * Monitoring modes - active, passive or manual
  * Start, stop and restart of programs
  * Group and manage groups of programs
  * Process dependency definition
  * Logging to syslog or own logfile
  * Configuration - comprehensive controlfile
  * Runtime and TCP/IP port checking (tcp and udp)
  * SSL support for port checking
  * Unix domain socket checking
  * Process status and process timeout
  * Process cpu usage
  * Process memory usage
  * Process zombie check
  * Check the systems load average
  * Check a file or directory timestamp
  * Alert, stop or restart a process based on its characteristics
  * MD5 checksum for programs started and stopped by monit
  * Alert notification for program timeout, restart, checksum, stop
    resource and timestamp error
  * Flexible and customizable email alert messages
  * Protocol verification. HTTP, FTP, SMTP, POP, IMAP, NNTP, SSH, DWP,
    LDAPv2 and LDAPv3
  * An http interface with optional SSL support to make monit
    accessible from a webbrowser

```

---

### Post by SwedishWings on 2008-11-23
Thanks Greyed,

that was another very interesting option. In particular, I like the flexibility like being able to monitor log file sizes etc. Very handy, thanks!

After reading a bit more about "upstart" (the Sys V "init" replacement in Ubuntu) i realized that there is a simple way to do this by adding a file to /etc/event.d/ looking something like this:
```

# myservice
start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /usr/bin/myservice
```

Is this the correct way of adding a service, or is this considered "hacking"? I can't find much doc's on this subject, so if anyone can tell me what the "standard" expects from services run like this, it would be most welcome.

Regards,
Mike

---

