---
title: "block port 80 incomming"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-05-25
how do i block port 80 (internet) that comes in so users will quit changing proxy settings. I know the easyest wasy would be to do it from the router but this is for a laptop.

ufw deny in 80
Rule updated
Rule added (v6)
Status: active
To                         Action      From
--                         ------      ----
80                         DENY        Anywhere
80                         DENY        Anywhere (v6)

but firefox can still get to google with out the proxy setting even added

Status: active
To                         Action      From
--                         ------      ----
80                         DENY        Anywhere
Anywhere                   ALLOW       10.18.12.17 8080
Anywhere                   ALLOW       10.18.12.17 3128
Anywhere                   ALLOW       10.18.12.17 80
80                         DENY        Anywhere (v6)

80                         DENY OUT    Anywhere
80                         DENY OUT    Anywhere (v6)


my proxy is at 10.18.12.17 8080 put the port 80 keeps working even with out the proxy settings. How ever if i close the outging port 80 then nothing works even with the proxy settings.

---

### Post by aktiwers on 2012-05-29
[http://www.cyberciti.biz/faq/iptables-block-port/](http://www.cyberciti.biz/faq/iptables-block-port/)

---

