---
title: "Zoneminder not sending emails of alarms"
date: 2020-04-14
forum: New to Ubuntu
---

### Post by khattingh-virginmediacom on 2020-04-14
Hi,Relative new to Ubuntu(4 Months).Ubuntu 18 and I managed to get Zoneminder v1.35.2 installed and working but for the sending of emails on alarms created.Went through nearly all of ZM literature but cannot find a solution.Logs shows that notification email created but no email is sent.I checked all the settings in filters and Options>email and cannot find success.Any help would be appreciated.Thanks

---

### Post by yancek on 2020-04-14
Have you tried the various options at the Zoneminder Wiki at the link below?

[https://wiki.zoneminder.com/SMS_Notifications](https://wiki.zoneminder.com/SMS_Notifications)

---

### Post by SeijiSensei on 2020-04-14
Are you running a mail exchanger like Postfix or sendmail on the host?  To where are these notifications supposed to be sent? Have you looked in root's mailbox, /var/spool/mail/root?

---

### Post by khattingh-virginmediacom on 2020-04-14
I have done all that.Can send you screenshots of my settings

---

### Post by khattingh-virginmediacom on 2020-04-14
I am using msmtp.Notifications must be sent to my gmail address.On entering /var/spool/mail/root I get a reply of:-bash: /var/spool/mail/root: Permission denied.I am in root

---

### Post by SeijiSensei on 2020-04-14
Maybe your ISP blocks outbound SMTP traffic on port 25.  Try this test.  From the server run the command
```
telnet gmail-smtp-in.l.google.com 25
```

Do you get back a reply from the GMail server, or does the connection attempt hang?

If you cannot connect, you need to talk to your ISP.

---

### Post by khattingh-virginmediacom on 2020-04-15
Get reply in Terminal of:Trying 142.250.13.26...
Connected to gmail-smtp-in.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP s83si14764336wms.147 - gsmtp
Nothing in Gmail itself

---

### Post by SeijiSensei on 2020-04-16
You can't type "/var/spool/mail/root" at the prompt because the shell will interpret as trying to run the "root" command in the directory /var/spool/mail.  You need to display it with a command like "more /var/spool/mail/root".

---

### Post by khattingh-virginmediacom on 2020-04-18
Sorry but I don't understand.I am not that well computer literate.I made a new filter and for a few hours the email was successfully sent but then stopped with message in the logs of:ERR Unable to send email:error closing /usr/lib/sendmail:Broken pipe(exit -1).Before it stopped at creating notification email

---

### Post by khattingh-virginmediacom on 2020-04-18
I think I got it working now.Thanks for your patience and help

---

### Post by khattingh-virginmediacom on 2020-04-19
Since 19h00 last night no emails sent.Why is it so difficult to get ZM to work properly?

---

