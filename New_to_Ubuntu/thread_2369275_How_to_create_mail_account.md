---
title: "How to create mail account?"
date: 2017-08-21
forum: New to Ubuntu
---

### Post by muazzamazaz on 2017-08-21
I have following postfix configuration and when I create a new ubuntu user, it didn't create mail directory.

```
root@veezphone.com's password:
Last login: Thu Aug 17 14:52:26 2017 from 182.186.8.72
root@veezphone:~# useradd -d /var/www/muazzam1 -g 515 -u 603 -s /sbin/nologin muazzam1
useradd: group '515' does not exist
root@veezphone:~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_size_limit = 0
message_size_limit = 20480000
mydestination = veezphone.com localhost.$mydomain $mydomain
myhostname = veezphone.com
mynetworks = 127.0.0.1, 62.75.170.62
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_host_lookup = native
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_transport = dovecot



```

---

### Post by TheFu on 2017-08-21
adduser or useradd (I always get those mixed up - one of them) supports adding scripts to the userid creation.  You can cause anything you need to occur in the script you create.  For example, neither command will add a userid to any LDAP server, so it is common to do that rather than let it modify the /etc/passwd, shadow, group and sgroup files.

Or if everything is self contained on the single server, then you can just modify the defaults for userid creation.  There are files controlling that in /etc/skel/ somewhere.  Also /etc/default/useradd.

useradd -m is needed to use the skel stuff - I think.  The manpages have the details.

Is is all under your control.  This type of stuff is normally covered in the 3rd LPI admin course.

---

