---
title: "[SOLVED] Apache2 not on internet"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by openjoel on 2008-05-02
Hello!
I'm trying to get my server working.
But have encountered some problems. Everything works...
Exept Apache2 over internet.

Things like ftp, ssh, webmin and shoutcast work fine.
And apache2 used to work for a while but suddenly just stoped!

I can access the apache2 root folder localy.
The port in my router is open.

PLEASE HELP ME!
I'm desperate!

---

### Post by rubicon on 2008-05-02
Be more specific, please.

Have you started apache? sudo apache2ctl start
Have you restarted it? sudo apache2ctl restart

Can you connect to [http://127.0.0.1/](http://127.0.0.1/) ? What error you get in browser? What */var/log/apache2/access.log* and */var/log/apache2/error.log* say?

---

### Post by openjoel on 2008-05-02
This is so wierd!
Apache2 work now! And I have not done anything!
Yes I can reach apache localy!

Hmm. Will get back if I find the cause!

---

