---
title: "Ubuntu server 14.04 openssh monitoring?"
date: 2014-10-21
forum: New to Ubuntu
---

### Post by chrhelling on 2014-10-21
Hi there, i have finally got my server up and running just like i want!
but i was wondering if the screen that is connected to my server can show what commands that have been typed and what files that are being transferred to and from the sftp server?

if you understand?
like i go on my computer sign in to ssh and punching out some commands.
when i then punch a command it will show up on the server monitor?

---

### Post by tgalati4 on 2014-10-21
```
history
cat /var/log/auth.log
```

Understand that if you suspect a compromise of your server, these files are easy to change and hide activity.

---

### Post by Lars Noodén on 2014-10-21
You could increase the [log level for the SFTP server](http://manpages.ubuntu.com/manpages/trusty/en/man5/sshd_config.5.html) if you want to see which files transfer:

```

Subsystem internal-sftp -l INFO

```

LogLevel VERBOSE ought to do it, too.  If you want to separate that log traffic then change the log facility as well and then filter it to its own file in rsyslog.

---

