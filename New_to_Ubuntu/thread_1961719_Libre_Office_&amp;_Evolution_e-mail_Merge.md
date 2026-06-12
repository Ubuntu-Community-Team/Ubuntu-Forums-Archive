---
title: "Libre Office &amp; Evolution e-mail Merge"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Glkanter on 2012-04-19
[SIZE=2]I'm trying this for the first time. This is the error message I'm getting:

```
<class 'smtplib.SMTPSenderRefused'>: (530, '5.7.0 Must issue a STARTTLS command first. de2sm520292igc.4', u'ffbcleve@gmail.com'), traceback follows
  /usr/lib/python2.7/smtplib.py:701 in function sendmail() [raise SMTPSenderRefused(code, resp, from_addr)]
  /usr/lib/libreoffice/basis-link/program/mailmerge.py:226 in function sendMailMessage() [self.server.sendmail(sendermail, truerecipients, msg.as_string())]

```It comes right after it attempts to generate the batch of e-mails. I'm using a gmail account that I set up for this purpose. 

And there is every possibility that I answered the merge configuration questions wrong.

Thanks!

Garry[/SIZE]

---

### Post by Glkanter on 2012-04-19
Maybe I have the gmail settings correct after all...

---

### Post by dzponce11 on 2012-04-19
What it's saying is that some command has to be issued by either you or the system. Not really sure, not a guru in this area.

---

