---
title: "Rotating LOG Files; messages, syslog.log &amp; kern.log"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by graphicpower on 2012-06-13
I want to rotate the log files;
/var/log/**syslog**
/var/log/**messages**
/var/log/**kern.log**

based on size, i.e., whenever the file reaches, e.g., 100M it should be rotated

I believe the configuration file responsible for them is  **/etc/logrotate.d/rsyslog**
and the default settings for syslog  for instance are;
[COLOR=Sienna]/var/log/syslog
{
        rotate 7
        daily
        missingok
        notifempty
        delaycompress
        compress
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}
[/COLOR]

Can I add the line   [COLOR=Red]**size  100M**[/COLOR]  in between?

and does the order of lines or settings mentioned above matter?! I mean does the size (if possible) must be before or after certain line/setting ?

Can I change from **daily  **to **hourly **or by using crontab ?
[I][COLOR=Blue]the reason I am asking for this because I had an issue with one of the faulty hardware that generated thousands of lines of error messages, which filled up the  **[COLOR=Red]/ [/COLOR]**  partition in minutes

[/COLOR][/I][COLOR=Blue][COLOR=Black]THANK YOU ...

[/COLOR][/COLOR]

---

