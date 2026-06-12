---
title: "Sending (not recieving) mail from command line"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2013-02-17
I want to send an email from a script. I don't now most of the stuff about mail or postfix or relays. And I don't want a mail server. I'm not looking at setting a mail server. Just a simple way to send emails to my gmail account from the command line.

I messed alot with postfix configuration and I got lost. Basically here is what I want to do:

```
echo something | mailx -s "test" mymail@google.com
```

And then get it at my gmail inbox.

However this is what i get in /var/log/mail.log

```

Feb 17 17:08:02 ubuntu postfix/pickup[4477]: 7381D181A27: uid=0 from=<root>
Feb 17 17:08:02 ubuntu postfix/cleanup[4483]: 7381D181A27: message-id=<20130217140802.7381D181A27@ubuntu>
Feb 17 17:08:02 ubuntu postfix/qmgr[4478]: 7381D181A27: from=<root@ubuntu>, size=279, nrcpt=1 (queue active)
Feb 17 17:08:03 ubuntu postfix/smtp[4485]: connect to gmail-smtp-in.l.google.com[2a00:1450:4008:c01::1b]:25: Network is unreachable
Feb 17 17:08:04 ubuntu postfix/smtp[4485]: 7381D181A27: to=<mymail@gmail.com>, relay=gmail-smtp-in.l.google.com[173.194.69.26]:25, delay=2, delays=0.1/0.01/0.89/1, dsn=5.7.1, status=bounced (host gmail-smtp-in.l.google.com[173.194.69.26] said: 550-5.7.1 [5.82.12.160] The IP you're using to send mail is not authorized to 550-5.7.1 send email directly to our servers. Please use the SMTP relay at your 550-5.7.1 service provider instead. Learn more at 550 5.7.1 http://support.google.com/mail/bin/answer.py?answer=10336 b14si43568710bka.19 - gsmtp (in reply to end of DATA command))
Feb 17 17:08:04 ubuntu postfix/cleanup[4483]: 7E8C3181A28: message-id=<20130217140804.7E8C3181A28@ubuntu>
Feb 17 17:08:04 ubuntu postfix/bounce[4486]: 7381D181A27: sender non-delivery notification: 7E8C3181A28
Feb 17 17:08:04 ubuntu postfix/qmgr[4478]: 7E8C3181A28: from=<>, size=2631, nrcpt=1 (queue active)
Feb 17 17:08:04 ubuntu postfix/qmgr[4478]: 7381D181A27: removed
Feb 17 17:08:04 ubuntu postfix/local[4487]: 7E8C3181A28: to=<root@ubuntu>, relay=local, delay=0.12, delays=0.07/0/0/0.05, dsn=2.0.0, status=sent (delivered to mailbox)
Feb 17 17:08:04 ubuntu postfix/qmgr[4478]: 7E8C3181A28: removed

```

any help?

---

### Post by sudodus on 2013-02-17
Try this link (I have not tried it myself but it looks convincing)

[[COLOR="Red"]http://tuxtweaks.com/2012/10/send-gmail-from-the-linux-command-line/[/COLOR]]("http://tuxtweaks.com/2012/10/send-gmail-from-the-linux-command-line/")

---

### Post by HermanAB on 2013-02-17
Mail, mutt and telnet can all be used to send mail from a script.

---

### Post by schragge on 2013-02-17
Configuring *postfix* to work with *gmail* is not a trivial task. See [this tutorial]("http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/"). BTW, are you sure you really need postfix? Instead, you can try *msmtp* as the how-to linked by **sudodus** suggests, or [ssmtp](http://manpages.ubuntu.com/manpages/precise/en/man5/ssmtp.conf.5.html). They are much easier to configure and comprehend.

[highlight]Update.[/highlight]
The error message from your log seems pretty clear to me:
> 
The IP you're using to send mail is not authorized to 550-5.7.1 send email directly to our servers. Please use the SMTP relay at your 550-5.7.1 service provider instead. Learn more at 550 5.7.1 [http://support.google.com/mail/bin/answer.py?answer=10336](http://support.google.com/mail/bin/answer.py?answer=10336)


---

### Post by steeldriver on 2013-02-17
agreed - I recently set up ssmtp so I can get mdadm status emails from my htpc

tbh I'm still a bit confused about the ssmtp.conf file - but it works

---

### Post by Abu_Dayya on 2013-02-17
> **schragge said:**
> Configuring *postfix* to work with *gmail* is not a trivial task. See [this tutorial]("http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/"). BTW, are you sure you really need postfix? Instead, you can try *msmtp* as the how-to linked by **sudodus** suggests, or [ssmtp](http://manpages.ubuntu.com/manpages/precise/en/man5/ssmtp.conf.5.html). They are much easier to configure and comprehend.

[highlight]Update.[/highlight]
The error message from your log seems pretty clear to me:


Thanks man.
Well does that mean I can't send emails to gmail at all? Even if I setup a mail server? Doesn't matter if its postfix or not.

---

### Post by schragge on 2013-02-17
I didn't say that. From the page at Google describing the problem:
> 
Another alternative is to send mail through your own domain’s servers, either by configuring them to allow relay from your IP address, or by using MSA (mail submission agent). Learn how to use Gmail to [send mail from a different address]("https://support.google.com/mail/bin/answer.py?hl=en&answer=22370").


BTW, have you tried the how-to linked above by **sudodus**?

---

### Post by Abu_Dayya on 2013-02-17
YESSS. Using msmtp-mta worked. Thanks all

One more question (getting greedy) If I want to send an email to another domain (something like [email]mymail@mydomain.com[/email]) I can tell what changes I should make. but what about those two lines in ~/.mailrc

set sendmail="/usr/bin/msmtp"
set message-sendmail-extra-arguments="-a gmail"

what do I use instead of gmail here? do I use mydomain?

Thanks a lot guys. really appreciated

---

### Post by sudodus on 2013-02-18
You can send messages to addresses other than @gmail. But the 'sender' will be your gmail account.

> You can also use a message saved in a text file rather than entering it interactively. This is especially useful if you're automating this process in a script. In this example, the email is saved in a file called message.txt.
```
mail -s "Subject" address@example.com < message.txt
```

---

