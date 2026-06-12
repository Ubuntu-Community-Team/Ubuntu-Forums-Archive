---
title: "ntp start in Hardy fixed?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by movrshakr on 2008-05-03
This is a question to someone who has Hardy installed and has not modified the ntp setup.  Gutsy had some real issues with start sequence of eth0, ntpdate and ntpd.  My questions are:

Is ntp (ntpd) 'ON' in a standard install?
For someone who has it running (look in syslog)...
 - does eth0 start only once and before ntpd starts
 - does ntpd start only once
 - does it get associated with a server(s) (run ntpq -p to see)
 - does ntpdate run one time before ntpd starts

Thanks

---

### Post by movrshakr on 2008-05-06
Touching the topic since there was no response for 2 days.

---

