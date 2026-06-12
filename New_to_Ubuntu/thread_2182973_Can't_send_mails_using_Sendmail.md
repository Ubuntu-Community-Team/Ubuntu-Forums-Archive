---
title: "Can't send mails using Sendmail"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by siddharth007 on 2013-10-23
Hi everyone,

I recently configured bugzilla on one of the servers.Now bugzilla needs to send a mail in case of a new account creation request.I have configured sendmail for this.However,while sending a mail to my internal mail server the syslogs showed up something like this 
```
Oct 23 05:42:26 Bugzilla sendmail[7168]: r9N9gPAv007168: from=www-data, size=1304, class=0, nrcpts=1, msgid=<201310230942.r9N9gPAv007168@Bugzilla.f*********.in>, relay=www-data@localhost
Oct 23 05:42:26 Bugzilla sm-mta[7170]: r9N9gQxx007170: from=<www-data@Bugzilla.f*********.in>, size=1569, class=0, nrcpts=1, msgid=<201310230942.r9N9gPAv007168@Bugzilla.f*********.in>, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Oct 23 05:42:27 Bugzilla sendmail[7168]: r9N9gPAv007168: to=si******@f********.in, ctladdr=www-data (33/33), delay=00:00:02, xdelay=00:00:01, mailer=relay, pri=31304, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (r9N9gQxx007170 Message accepted for delivery)
Oct 23 05:42:27 Bugzilla sm-mta[7173]: STARTTLS=client, relay=mx.f*********.in., version=TLSv1/SSLv3, verify=FAIL, cipher=AES128-SHA, bits=128/128
Oct 23 05:42:34 Bugzilla sm-mta[7173]: r9N9gQxx007170: to=<s******@f*********.in>, ctladdr=<www-data@Bugzilla.f**********.in> (33/33), delay=00:00:08, xdelay=00:00:07, mailer=esmtp, pri=121569, relay=mx.f**********.in. [172.73.**.**], dsn=5.0.0, stat=Service unavailable
Oct 23 05:42:34 Bugzilla sm-mta[7173]: r9N9gQxx007170: r9N9gYxx007173: DSN: Service unavailable
Oct 23 05:42:34 Bugzilla sm-mta[7173]: r9N9gYxx007173: to=<www-data@Bugzilla.f************.in>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

```

Looks like its not a sendmail problem,but somehow it is not able to send a mail to destination.What could be the reason behind this? Desperately need a help on this.

---

### Post by TheFu on 2013-10-23
You are posting this inside the "Absolute Beginners" section. Sendmail is NOT for beginners or even intermediate admins. 
I'd highly recommend against using sendmail until after you outgrow postfix.  Postfix provides a sendmail compatible interface and does 95% of what sendmail can do, but was written from the ground up to be secure.

After all that is said, sending email is not a trivial thing.  Most ISPs block outbound email, except through authenticated accounts AND only if it goes through a gateway. The receiving systems all work hard to avoid spammers. I do.  Talk with your email administrator about allowing emails from internal server subnets to internal-only email addresses.

---

