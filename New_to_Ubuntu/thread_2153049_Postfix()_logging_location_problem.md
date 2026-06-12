---
title: "Postfix(?) logging location problem"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by pauliolio on 2013-06-10
We have a vps running Ubuntu 10.04.4 LTS, and while trying to find a solution to a php problem, I've become aware of what looks like a problem with the syslog system - I'm not sure though.


The syslog.conf file looks like this:


```
    auth,authpriv.*      -/var/log/auth.log
*.*;auth,authpriv.none  -/var/log/syslog
#cron.*          -/var/log/cron.log
daemon.*            -/var/log/daemon.log
kern.*              -/var/log/kern.log
lpr.*               -/var/log/lpr.log
mail.*              -/opt/psa/var/log/maillog
user.*              -/var/log/user.log


#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info           -/var/log/mail.info
mail.warning            -/var/log/mail.warn
mail.err         -/var/log/mail.err




# Logging for INN news system
#
news.crit        -/var/log/news/news.crit
news.err         -/var/log/news/news.err
news.notice         -/var/log/news/news.notice


#
# Some `catch-all' logfiles.
#
*.=debug;\
    auth,authpriv.none;\
    news.none;mail.none -/var/log/debug
*.=info;*.=notice;*.=warning;\
    auth,authpriv.none;\
    cron,daemon.none;\
    mail,news.none      -/var/log/messages


#
# Emergencies are sent to everybody logged in.
#
*.emerg             *


#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#   news.=crit;news.=err;news.=notice;\
#   *.=debug;*.=info;\
#   *.=notice;*.=warning    /dev/tty8


# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
    news.err;\
    *.=debug;*.=info;\
    *.=notice;*.=warning    |/dev/xconsole



```

And the /var/log/syslog file contains loads of entries like this:


Jun 10 04:04:00 lvps109-104-93-171 postfix/qmgr[688]: 814E0676E997: removed
Jun 10 04:04:01 lvps109-104-93-171 postfix/smtpd[11105]: connect from mail-we0-f196.google.com[74.125.82.196]

/var/log/mail.info, /var/log/mail.warn, & /var/log/mail.err are all empty despite the above configuration directing the relevant messages to them.


I've tried adding 'mail.* -/var/log/mail.log' to the conf file to see whether I can get the smtp & qmgr messages repeated there, but that log file remains empty too.


I tried changing '.;auth,authpriv.none -/var/log/syslog' to .;auth,authpriv.none;mail.none -/var/log/syslog to see whether I could stop any postfix messages going into /var/log/syslog, but they continue to go there.


I've been searching for ages to find the command I need to redirect these postfix messages to the mail.log file, but posts I've found only seem to mention the .info, .err, & .warn messages. As far as I have been able to find out , the syslog daemon should be directing them to the relevant files.


So my questions are: How do I redirect the postfix messages away from /var/log/syslog? Why aren't the .warn, .info, & .err messages going where they should be?


Any help gratefully received - Many thanks.

---

