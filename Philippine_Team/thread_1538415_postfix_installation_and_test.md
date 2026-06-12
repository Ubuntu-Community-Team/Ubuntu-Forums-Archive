---
title: "postfix installation and test"
date: 2010-07-25
forum: Philippine Team
---

### Post by WINPINPH1 on 2010-07-25
sir i need guide in testing my postfix

my dns = mwit.no-ip.biz
portforwarded ng ang port 25 sa router
up and running na ang webserver ko.

postfix initial configuration:


edwin@edwin-desktop:/etc/postfix$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command =
mailbox_size_limit = 0
mydestination = mwit.no-ip.biz, edwin-desktop, localhost.localdomain, localhost
myhostname = mwit.no-ip.biz
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom



paturo po kung paano ko ma test ito kung maka receive nako ng mail from internet at saang directory ko makikita yung mail.
and paano ako mag send ng mail sa internet.

kahit test ko sa ym ko na [email]jigsneth@yahoo.com[/email]

tia.

---

