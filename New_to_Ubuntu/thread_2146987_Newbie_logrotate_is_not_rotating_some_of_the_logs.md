---
title: "Newbie: logrotate is not rotating some of the logs"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by supremedalek on 2013-05-20
I am saying "some" because I do not want to check if all the logs are not being properly rotated. Anywhoo, the trivial question of the day has to do with logrotate. Let's say /etc/logrotate.d/rsyslog  looks like this:
```
/var/log/syslog/syslog.log
/var/log/mail/mail.info
/var/log/mail/mail.warn
/var/log/mail/mail.err
/var/log/mail/mail.log
/var/log/auth/auth.log
/var/log/user/user.log
/var/log/daemon/daemon.log
/var/log/kern/kern.log
/var/log/lpr/lpr.log
/var/log/debug/debug.log
/var/log/messages/messages.log
/var/log/apache2/access.log
/var/log/apache2/error.log
/var/log/keygend/keygend.log
/var/log/fail2ban/fail2ban.log
{
        dateformat -%Y-%m-%d
        daily
        compress
        maxage 360
        rotate 360
        missingok
        dateext
        sharedscripts
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
```

Nothing special to it so far (yeah, the directories have been created and rsyslog has been configured to use them). Based on what I read in [http://serverfault.com/questions/375004/logrotate-not-rotating-the-logs](http://serverfault.com/questions/375004/logrotate-not-rotating-the-logs), I go to /var/lib/logrotate/status and edit the syslog line to say last time it ran was yesterday:

```
"/var/log/syslog/syslog.log" 2013-5-19
```

And then run logrotate manually for rsyslog only:
```
logrotate -v -f /etc/logrotate.d/rsyslog 
reading config file /etc/logrotate.d/rsyslog
reading config info for /var/log/syslog/syslog.log
/var/log/mail/mail.info
/var/log/mail/mail.warn
/var/log/mail/mail.err
/var/log/mail/mail.log
/var/log/auth/auth.log
/var/log/user/user.log
/var/log/daemon/daemon.log
/var/log/kern/kern.log
/var/log/lpr/lpr.log
/var/log/debug/debug.log
/var/log/messages/messages.log
/var/log/apache2/access.log
/var/log/apache2/error.log
/var/log/keygend/keygend.log
/var/log/fail2ban/fail2ban.log


Handling 1 logs

rotating pattern: /var/log/syslog/syslog.log
/var/log/mail/mail.info
/var/log/mail/mail.warn
/var/log/mail/mail.err
/var/log/mail/mail.log
/var/log/auth/auth.log
/var/log/user/user.log
/var/log/daemon/daemon.log
/var/log/kern/kern.log
/var/log/lpr/lpr.log
/var/log/debug/debug.log
/var/log/messages/messages.log
/var/log/apache2/access.log
/var/log/apache2/error.log
/var/log/keygend/keygend.log
/var/log/fail2ban/fail2ban.log
 forced from command line (360 rotations)
empty log files are rotated, old logs are removed
considering log /var/log/syslog/syslog.log
  log needs rotating
considering log /var/log/mail/mail.info
  log needs rotating
considering log /var/log/mail/mail.warn
  log needs rotating
considering log /var/log/mail/mail.err
  log needs rotating
considering log /var/log/mail/mail.log
  log needs rotating
considering log /var/log/auth/auth.log
  log needs rotating
considering log /var/log/user/user.log
  log needs rotating
considering log /var/log/daemon/daemon.log
  log needs rotating
considering log /var/log/kern/kern.log
  log needs rotating
considering log /var/log/lpr/lpr.log
  log needs rotating
considering log /var/log/debug/debug.log
  log needs rotating
considering log /var/log/messages/messages.log
  log needs rotating
considering log /var/log/apache2/access.log
  log needs rotating
considering log /var/log/apache2/error.log
  log needs rotating
considering log /var/log/keygend/keygend.log
  log needs rotating
considering log /var/log/fail2ban/fail2ban.log
  log needs rotating
rotating log /var/log/syslog/syslog.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
rotating log /var/log/mail/mail.info, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/mail/mail.info-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/mail/mail.warn, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/mail/mail.warn-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/mail/mail.err, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/mail/mail.err-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/mail/mail.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/mail/mail.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/auth/auth.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/auth/auth.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/user/user.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/user/user.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/daemon/daemon.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/daemon/daemon.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/kern/kern.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/kern/kern.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/lpr/lpr.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/lpr/lpr.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/debug/debug.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/debug/debug.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/messages/messages.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/messages/messages.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/apache2/access.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/apache2/access.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/apache2/error.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/apache2/error.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/keygend/keygend.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/keygend/keygend.log-2013-05-20.gz already exists, skipping rotation
rotating log /var/log/fail2ban/fail2ban.log, log->rotateCount is 360
Converted ' -%Y-%m-%d' -> '-%Y-%m-%d'
dateext suffix '-2013-05-20'
glob pattern '-[0-9][0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9]'
destination /var/log/fail2ban/fail2ban.log-2013-05-20.gz already exists, skipping rotation
```

syslog.log-2013-05-20.gz is not created:
```
ls -lh /var/log/syslog/syslog.log-2013-05-20.gz
ls: cannot access /var/log/syslog/syslog.log-2013-05-20.gz: No such file or directory
```
Why?

---

