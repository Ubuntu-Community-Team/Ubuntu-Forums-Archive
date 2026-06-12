---
title: "443 Port not listen"
date: 2013-10-16
forum: New to Ubuntu
---

### Post by Stanley_Ho on 2013-10-16
Dear all,

I just install Ubuntu 12.04.3 LTS.  After installation, I used the netstat -an|grep 80 and returns 0.0.0.0:80.  It's normal but I used netstat -an|grep 443 no output here.  I have checked all listen ports but I can't find 443.  Is there any configuration to be done?  No idea for 443 port not ready?  Please advise.

Regards
Stanley

---

### Post by Doug S on 2013-10-17
Hi Stanley,

And welcome to Ubuntu forums.

The apache web server does not listen on port 443 (HTTPS) by default. You will have to enable it and create certificates and such.
The [Ubuntu server guide]("https://help.ubuntu.com/13.10/serverguide/httpd.html#https-configuration") is a good reference (The link is to the 13.10 edition, even though you mentioned 12.04.3)

---

