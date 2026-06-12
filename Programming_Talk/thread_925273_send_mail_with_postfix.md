---
title: "send mail with postfix"
date: 2008-09-20
forum: Programming Talk
---

### Post by davidtuti on 2008-09-20
Hi,
I configure a postfix to can send mail from command-line whith this howto

[http://www.drfest.com.ar/2008/02/howto-postfix-utilizando-gmail-como.html](http://www.drfest.com.ar/2008/02/howto-postfix-utilizando-gmail-como.html)

I try to send mail:

mailx -s Descarga [email]pepe@gmail.com[/email] < mensaje

but the mail doesn't arrive

The log:

Sep 20 10:30:40 ubuntu postfix/pickup[7553]: 365EA8F1F4: uid=1000 from=<david>
Sep 20 10:30:40 ubuntu postfix/cleanup[7636]: 365EA8F1F4: message-id=<20080920173040.365EA8F1F4@ubuntu>
Sep 20 10:30:40 ubuntu postfix/qmgr[7554]: 365EA8F1F4: from=<david@ubuntu>, size=272, nrcpt=1 (queue active)
Sep 20 10:30:44 ubuntu postfix/smtp[7638]: 365EA8F1F4: to=<pepe@gmail.com>, relay=gmail-smtp-in.l.google.com[66.249.93.27]:25, delay=3.8, delays=0.05/0.01/0.5/3.2, dsn=5.1.1, status=bounced (host gmail-smtp-in.l.google.com[66.249.93.27] said: 550-5.1.1 The email account that you tried to reach does not exist. Please 550-5.1.1 try double-checking the recipient's email address for typos 550-5.1.1 or unnecessary spaces. Learn more at                      550 5.1.1 [http://mail.google.com/support/bin/answer.py?answer=6596](http://mail.google.com/support/bin/answer.py?answer=6596) a1si5330989ugf.37 (in reply to RCPT TO command))
Sep 20 10:30:44 ubuntu postfix/cleanup[7636]: 16A638F1F5: message-id=<20080920173044.16A638F1F5@ubuntu>
Sep 20 10:30:44 ubuntu postfix/qmgr[7554]: 16A638F1F5: from=<>, size=2532, nrcpt=1 (queue active)
Sep 20 10:30:44 ubuntu postfix/bounce[7640]: 365EA8F1F4: sender non-delivery notification: 16A638F1F5
Sep 20 10:30:44 ubuntu postfix/qmgr[7554]: 365EA8F1F4: removed
Sep 20 10:30:44 ubuntu postfix/local[7641]: 16A638F1F5: to=<david@ubuntu>, relay=local, delay=0.03, delays=0.01/0.01/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Sep 20 10:30:44 ubuntu postfix/qmgr[7554]: 16A638F1F5: removed


My configuration is:

postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = ubuntu, localhost.localdomain, , localhost
myhostname = ubuntu
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

Any help? 

Many thanks and sorry for me english!

---

### Post by estamand on 2008-09-20
I'm no expert when it comes to email servers but this error in the message "The email account that you tried to reach does not exist." tells me that [email]pepe@gmail.com[/email] is not a valid email address?

---

### Post by davidtuti on 2008-09-20
Sorry I have a mistake

This is the log:

Sep 20 11:20:17 ubuntu postfix/pickup[6171]: 5C56B8F1F5: uid=1000 from=<david>
Sep 20 11:20:17 ubuntu postfix/cleanup[7503]: 5C56B8F1F5: message-id=<20080920182017.5C56B8F1F5@ubuntu>
Sep 20 11:20:17 ubuntu postfix/qmgr[6173]: 5C56B8F1F5: from=<david@ubuntu>, size=278, nrcpt=1 (queue active)
Sep 20 11:20:22 ubuntu postfix/smtp[7505]: 5C56B8F1F5: to=<mierdatuti@gmail.com>, relay=gmail-smtp-in.l.google.com[64.233.183.27]:25, delay=5.4, delays=0.11/0.02/0.62/4.7, dsn=5.7.1, status=bounced (host gmail-smtp-in.l.google.com[64.233.183.27] said: 550-5.7.1 [87.220.178.188] The IP you're using to send mail is not authorized 550-5.7.1 to send email directly to our servers. Please use the SMTP 550-5.7.1 relay at your service provider instead. Learn more at     550 5.7.1 [http://mail.google.com/support/bin/answer.py?answer=10336](http://mail.google.com/support/bin/answer.py?answer=10336) h6si14929308nfh.21 (in reply to end of DATA command))
Sep 20 11:20:22 ubuntu postfix/cleanup[7503]: B7EF28F1F6: message-id=<20080920182022.B7EF28F1F6@ubuntu>
Sep 20 11:20:22 ubuntu postfix/qmgr[6173]: B7EF28F1F6: from=<>, size=2585, nrcpt=1 (queue active)
Sep 20 11:20:22 ubuntu postfix/bounce[7521]: 5C56B8F1F5: sender non-delivery notification: B7EF28F1F6
Sep 20 11:20:22 ubuntu postfix/qmgr[6173]: 5C56B8F1F5: removed
Sep 20 11:20:22 ubuntu postfix/local[7522]: B7EF28F1F6: to=<david@ubuntu>, relay=local, delay=0.21, delays=0.03/0.14/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Sep 20 11:20:22 ubuntu postfix/qmgr[6173]: B7EF28F1F6: removed

Thanks!


EDIT---------------------------------------------------------------------------------------------------------------

I have changed the parameter 
relay host = smtp.gmail.com:587

Now the emaul doesnt arrive but I have other log:

Sep 22 11:01:39 ubuntu postfix/pickup[6151]: BF86E8F1F3: uid=1000 from=<david>
Sep 22 11:01:39 ubuntu postfix/cleanup[7727]: BF86E8F1F3: message-id=<20080922180139.BF86E8F1F3@ubuntu>
Sep 22 11:01:39 ubuntu postfix/qmgr[6153]: BF86E8F1F3: from=<david@ubuntu>, size=463, nrcpt=1 (queue active)
Sep 22 11:01:44 ubuntu postfix/smtp[7729]: BF86E8F1F3: to=<davidtuti@gmail.com>, relay=smtp.gmail.com[216.239.59.109]:587, delay=5, delays=0.05/0.01/4.8/0.09, dsn=5.7.0, status=bounced (host smtp.gmail.com[216.239.59.109] said: 530 5.7.0 Must issue a STARTTLS command first. m5sm772264gve.3 (in reply to MAIL FROM command))
Sep 22 11:01:44 ubuntu postfix/cleanup[7727]: DD2E08F1FE: message-id=<20080922180144.DD2E08F1FE@ubuntu>
Sep 22 11:01:44 ubuntu postfix/qmgr[6153]: DD2E08F1FE: from=<>, size=2234, nrcpt=1 (queue active)
Sep 22 11:01:44 ubuntu postfix/bounce[7730]: BF86E8F1F3: sender non-delivery notification: DD2E08F1FE
Sep 22 11:01:44 ubuntu postfix/qmgr[6153]: BF86E8F1F3: removed
Sep 22 11:01:44 ubuntu postfix/local[7731]: warning: database /etc/aliases.db is older than source file /etc/aliases
Sep 22 11:01:44 ubuntu postfix/local[7731]: DD2E08F1FE: to=<david@ubuntu>, relay=local, delay=0.03, delays=0.01/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Sep 22 11:01:44 ubuntu postfix/qmgr[6153]: DD2E08F1FE: removed


Some help?
Thanks a lot!

---

### Post by estamand on 2008-09-23
Looks like Gmail SMTP is lookin for a STARTTLS command. I'm guessing to start a secure/encrypted connection.

---

