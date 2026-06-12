---
title: "Sendmail fails (SYSERR(root): collect: Cannot write)"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by Houmie on 2013-06-28
Hey guys,

I am suffering since last night on this issue.  I have finally set up send mail.

and when i try to send a test mail lik ethis:

```
echo "My test email being sent from sendmail" | /usr/sbin/sendmail test@gmail.com
```

I get this error message:

```
Jun 28 11:27:05 tp sendmail[14101]: r5SAR5il014101: from=hooman, size=39, class=0, nrcpts=1, msgid=<201306281027.r5SAR5il014101@localhost.localdomain>, relay=hooman@localhost
Jun 28 11:27:05 tp sm-mta[14102]: r5SAR5jL014102: SYSERR(root): collect: Cannot write ./dfr5SAR5jL014102 (bfcommit, uid=0, gid=129): No such file or directory
Jun 28 11:27:05 tp sm-mta[14102]: r5SAR5jL014102: from=<hooman@localhost.localdomain>, size=342, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=localhost.localdomain [127.0.0.1]
Jun 28 11:27:05 tp sendmail[14101]: r5SAR5il014101: to=test@gmail.com, ctladdr=hooman (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30039, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfr5SAR5jL014102 (bfcommit, uid=0, gid=129): No such file or directory
```

Why can't sendmail "write"?  What do i do?

Many thanks,
Hooman

---

### Post by SeijiSensei on 2013-06-28
Does it work with "sudo echo ..."?

---

