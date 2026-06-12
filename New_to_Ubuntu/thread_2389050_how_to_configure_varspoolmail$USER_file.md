---
title: "how to configure /var/spool/mail/$USER file"
date: 2018-04-10
forum: New to Ubuntu
---

### Post by softengstu115 on 2018-04-10
Hello,

I'm new to Linux and I'm working on a bash script that checks for new mail in the mail spool file. 

When I try ls -l /var/spool/mail/ I get total 0.

Is there a way to configure a mail spool file so I can run my script to check for new entries in the mail spool file?

Any help would be appreciated!

---

### Post by SeijiSensei on 2018-04-10
Is this directory on your server? Are you running a mail exchanger like Postfix or sendmail?

If so, try installing the mailutils package, then send yourself an email with

```
echo test | mail -s test yourusername
```

You should see a /var/spool/mail/yourusername file with the contents of this test message. If you don't, take a look at /var/log/mail.log.

---

### Post by softengstu115 on 2018-04-10
> **SeijiSensei said:**
> Is this directory on your server? Are you running a mail exchanger like Postfix or sendmail?

If so, try installing the mailutils package, then send yourself an email with

```
echo test | mail -s test yourusername
```

You should see a /var/spool/mail/yourusername file with the contents of this test message. If you don't, take a look at /var/log/mail.log.

That worked, thank you! 
I had sendmail installed but I didn't have the mailutils package.

---

