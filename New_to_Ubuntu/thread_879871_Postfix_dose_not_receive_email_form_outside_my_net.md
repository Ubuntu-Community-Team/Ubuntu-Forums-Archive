---
title: "Postfix dose not receive email form outside my network"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by kofiernest on 2008-08-04
Hello I am totally a beginner I setup postfix with [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04") and I can send email outside my network but I can not receive mail from out network can I get help

Thanks in advance

---

### Post by dca on 2008-08-04
If you can send outside of your network into the real world but can not receive emails back, the problem could be port #25 (SMTP) is blocked...

---

### Post by Gone fishing on 2008-08-04
I take it the PC has direct access to the internet - not fire walled (you will need to open the port), you have a fixed IP and reverse lookup associating your domain name with the IP of the mail server?

---

### Post by maltairspace.com on 2009-10-05
Hi,

I have the same problem, I have set-up a Postfix + Dovecot mail server which took me quite a long time to get it running as I was rather new to linux.  Finally I sorted everything but I am missing one problem.

I can send and receive emails within my network and I also can send externally but I cannot send or receive from externally.  Although today funily enough I found out that when I send a mail from our mail server at work I received it.


alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
inet_interfaces = all
mailbox_size_limit = 0
myhostname = server.example.com
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = no
receive_override_options = no_address_mappings
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/postfix.pem
smtpd_tls_key_file = /etc/ssl/private/postfix.pem
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_gid_maps = static:6000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = dovecot
virtual_uid_maps = static:6000


Here is a copy of my postdonf -n

Thanks

---

