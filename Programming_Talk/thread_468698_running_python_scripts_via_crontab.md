---
title: "running python scripts via crontab"
date: 2007-06-09
forum: Programming Talk
---

### Post by littlephil56 on 2007-06-09
Hello all,
I wrote a simple python script to send mail via smtp to my gmail acc.I can run it as python /home/phil/Desktop/smtp.py but when I add the same to my crontab as
 >  * * * * * /usr/bin/python2.5 /home/phil/Desktop/smtp.py ,it doesn't run.I checked the process by using top command and python did start a thread but died soon.

I need some help here.

Here is the python script.It uses tls-lite to send mail over smtp

```
#!/usr/bin/env python
from tlslite.integration.SMTP_TLS import SMTP_TLS
import string, sys

class XSMTP_TLS(SMTP_TLS):

    def sendmail(self, from_addr, to_addrs, msg, mail_options=[],
                 rcpt_options=[]):

        if self.helo_resp is None and self.ehlo_resp is None:
            if not (200 <= self.ehlo()[0] <= 299):
                (code,resp) = self.helo()
                if not (200 <= code <= 299):
                    raise SMTPHeloError(code, resp)
        esmtp_opts = []
        if self.does_esmtp:
            # Hmmm? what's this? -ddm
            # self.esmtp_features['7bit']=""
            if self.has_extn('size'):
                esmtp_opts.append("size=%d" % len(msg))
            for option in mail_options:
                esmtp_opts.append(option)

        self.starttls()
        self.ehlo()
        self.login('uname@gmail.com', 'passwd')

 
        (code,resp) = self.mail(from_addr, esmtp_opts)
        if code != 250:
            self.rset()
            raise SMTPSenderRefused(code, resp, from_addr)
        senderrs={}
        if isinstance(to_addrs, basestring):
            to_addrs = [to_addrs]
        for each in to_addrs:
            (code,resp)=self.rcpt(each, rcpt_options)
            if (code != 250) and (code != 251):
                senderrs[each]=(code,resp)
        if len(senderrs)==len(to_addrs):
            # the server refused all our recipients
            self.rset()
            raise SMTPRecipientsRefused(senderrs)
        (code,resp) = self.data(msg)
        if code != 250:
            self.rset()
            raise SMTPDataError(code, resp)
        #if we got here then somebody got our mail
        return senderrs

 

if __name__=='__main__':
    connection= XSMTP_TLS('smtp.gmail.com',587)
    connection.set_debuglevel(1)
    #msg = ("From: from@gmail.com \r\nTo: toadd@gmail.com \r\n")
    FROM = "fromadd@gmail.com"
    TO = "toadd@gmail.com"

    SUBJECT = "for your information!"

    BODY = "body of the message"

    body = string.join((
    "From: %s" % FROM,
    "To: %s" % TO,
    "Subject: %s" % SUBJECT,
    "",
    BODY), "\r\n")
   
    connection.sendmail("fromadd@gmail.com","toaddr@gmail.com",body)
```

---

### Post by neojinux on 2007-06-09
Hi, 

I'm able to run it as cron job. Here is the simple line

* * *   *   *     ~/py/gmail_smtp.py

maybe you need to chmod +x for the script

Good Luck

---

### Post by littlephil56 on 2007-06-09
Something funny is happening.I have a write operation in the pythin script.So every minute the script is writing the file but it is not sending the mail.

Any ideas why?

---

### Post by GTvulse on 2007-06-09
> **littlephil56 said:**
> Something funny is happening.I have a write operation in the pythin script.So every minute the script is writing the file but it is not sending the mail.

Any ideas why?

Yes, you are not following the RFC spec. Either send two CRLF or a period and a CRLF to signal end-of-message.

---

### Post by littlephil56 on 2007-06-09
> **dradul said:**
> Yes, you are not following the RFC spec. Either send two CRLF or a period and a CRLF to signal end-of-message.

I didn't get that.How am I suppose to do that?

---

### Post by littlephil56 on 2007-06-09
Here's the output when I execute it directly:
> 
data: (354, 'Go ahead')
send: 'From: [email]fromaddr@gmail.com[/email]\r\nTo: [email]toaddr@gmail.com[/email]\r\nSubject: for your information!\r\n\r\nThis is the body \r\n.\r\n'
reply: '250 2.0.0 OK 1181405842 j7sm6774154wah\r\n'


I'm sending two crlf's ?ain't I ?
This is my first time with python .I may sound funny . :)

---

### Post by GTvulse on 2007-06-09
Make that \r\n\r\n.\r\n at the end of the message.

---

### Post by littlephil56 on 2007-06-09
> **dradul said:**
> Make that \r\n\r\n.\r\n at the end of the message.

Nah :( It didn't work.My firewall shows that m,y script is connecting to gmail but nothing happens after that. :(

---

