---
title: "Postfix: delivering local mails"
date: 2016-09-21
forum: New to Ubuntu
---

### Post by Luca_Brasi on 2016-09-21
Hi! I use POSFIX through relay and have some troubles with delivering. When system try to send mail for me (for example to andrew@mech-engineer) it goes to "mail.ru" server. After that it comes back to my relay address and marked like "Undelivered email"
I dont want it, i try to make exception for local mails. I wish get local mails direct to pc not through relay.

my **main.cf** is below. Thanks!


```
#myorigin = /etc/mailname
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mech-engineer, localhost
mydomain = mail.ru
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

# Relaying Postfix SMTP via mail.ru
relayhost = [smtp.mail.ru]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes

```

---

### Post by HermanAB on 2016-09-22
The answer is out there Scully...

[http://www.postfix.org/STANDARD_CONFIGURATION_README.html](http://www.postfix.org/STANDARD_CONFIGURATION_README.html)

[http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html)

Check all the mynetworks setings.

---

