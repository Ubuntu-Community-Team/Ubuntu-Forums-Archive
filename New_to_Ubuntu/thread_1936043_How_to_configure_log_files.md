---
title: "How to configure log files"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by Diametric on 2012-03-05
Hello,

Back in the day, there used to be a file in /etc called syslog.conf that allowed to you tom manage how your various log files were written to.   I see that that now is no longer the case.  How are they now managed?

Thank you!

---

### Post by Elfy on 2012-03-05
Changed apparently - though I only know that by having a look, never bothered fiddling with that one.

/etc/rsyslog.conf

also

/etc/rsyslog.d/50-default.conf

---

### Post by Diametric on 2012-03-05
Cool.  Thank you - that was what I was looking for.  I found this while looking around - 

located in: /usr/share/doc/rsyslog is a README.Debian that mentions the following

"The default configuration file for rsyslog is /etc/rsyslog.conf.

Its format is based on the standard syslog.conf format."

Cheers....

---

### Post by Elfy on 2012-03-05
Welcome :)

---

