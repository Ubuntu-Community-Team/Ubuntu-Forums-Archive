---
title: "mail delivery errors"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2012-02-17
This is kind of an embarrassing problem, because I should know how to fix it myself, but I don't.

I recently set up exim4 on a development server I have running Ubuntu.  I set it up to send mail using gmail's smtp so that I could test some of the mail functions of a project I was working on.

Now I'm getting mail delivery errors in my gmail account daily, saying that messages were not delivered to [email]root@(username).com[/email] and [email]www-data@(username).com[/email]

I can't remember where the settings would be to change these addresses so it doesn't try to send to them anymore.  I've checked in /etc/aliases, but it wasn't there.

There are two folders - root and www-data - in my /var/mail directory.  If I delete those, will that fix the problem?

---

### Post by SeijiSensei on 2012-02-17
What process is sending these messages?  Are they coming from cron?  If so, you can set the MAILTO environment variable at the top of a crontab to point to any address you want.  

It sounds like your exim implementation doesn't know how to handle local delivery, or else it's sending two copies of each message, one to the local user root and another to [email]root@domain.name[/email] which is undeliverable.  If you look at /var/mail/root, do you see the same messages which are generating delivery problems as [email]root@domain.name[/email], or are these sets of messages entirely distinct from one another?

---

### Post by stoogiebuncho on 2012-02-17
> **SeijiSensei said:**
> What process is sending these messages?  Are they coming from cron?  If so, you can set the MAILTO environment variable at the top of a crontab to point to any address you want.  
Yes, they are coming from cron.  My crontab doesn't have a MAILTO variable, but I assume I can just add one under the SHELL and PATH variables?  If I add a MAILTO variable but leave it a blank string, will it stop trying to send emails entirely?

> 
It sounds like your exim implementation doesn't know how to handle local delivery, or else it's sending two copies of each message, one to the local user root and another to [email]root@domain.name[/email] which is undeliverable.  If you look at /var/mail/root, do you see the same messages which are generating delivery problems as [email]root@domain.name[/email], or are these sets of messages entirely distinct from one another?
Yes, the messages are the same.

Thanks.

---

### Post by SeijiSensei on 2012-02-18
Cron mails error messages that aren't trapped by the commands it runs.  The easiest way to stop these messages is to pipe any output, including most importantly error output, to a log file like this:

```
* * * * * /path/to/myscript >> /var/log/myscript.log 2>&1
```

That sends any unexpected output from myscript to a log file; the "2>&1" item redirects error messages ("syserr") to the same file.

---

