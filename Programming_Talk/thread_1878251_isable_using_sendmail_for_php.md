---
title: "isable using sendmail for php"
date: 2011-11-09
forum: Programming Talk
---

### Post by ccflor on 2011-11-09
**Disable sendmail for php when send email**             
             
Hello,
I have a webserver with apache/php/mysql. I have configured the php.ini with statment
[mail function]
; For Win32 only.
; [http://php.net/smtp](http://php.net/smtp)
;SMTP = localhost
SMTP = my-own.mailserver.com
;SMTP = 192.168.200.10
; [http://php.net/smtp-port](http://php.net/smtp-port)
smtp_port = 25

; For Win32 only.
; [http://php.net/sendmail-from](http://php.net/sendmail-from)
sendmail_from = [EMAIL="Myaddress@emailserver.com"]Myaddress@emailserver.com[/EMAIL]


The emails are not working.
The conectivity beetwen webserver and email server is ok .
I see that php still try to use sendmail even if sendmail are started.
What should I do?
Thanks

---

### Post by Bachstelze on 2011-11-09
What part of "For Win32 only" do you not understand? For *NIX, you have to install Sendmail or a compatible MTA (Postfix, Exim...).

---

### Post by ccflor on 2011-11-12
> **Bachstelze said:**
> What part of "For Win32 only" do you not understand? For *NIX, you have to install Sendmail or a compatible MTA (Postfix, Exim...).

My question was about using a remote server for sending email from my website.  The problem was solved.

---

