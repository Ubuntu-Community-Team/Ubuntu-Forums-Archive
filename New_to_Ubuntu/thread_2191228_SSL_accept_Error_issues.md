---
title: "SSL_accept Error issues"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by cid420 on 2013-12-01
I can telnet localhost 25, but cannot etho localhost I get the connection closed by foreign host. I am trying to get the STARTTLS and Auth showso this is the reason I am having issues on receiving emails back from the outside. So here is my mail log

/etc/postfix/main.cf

[HTML]
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = fever.dyndns.info
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = fever.dyndns.info, localhost.dyndns.info, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = fever.dyndns.info, localhost.dyndns.info, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
[/HTML]

telnet localhost 25

[HTML]
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
etho localhost
Connection closed by foreign host.
[/HTML]



/var/log/mail.log

[HTML]
Dec  1 14:24:25 fever dovecot: imap-login: Login: user=<wlee1970>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=11616, secured
Dec  1 14:24:25 fever dovecot: imap(wlee1970): Disconnected: Logged out bytes=79/681
Dec  1 14:26:27 fever postfix/master[10752]: reload -- version 2.9.6, configuration /etc/postfix
Dec  1 14:26:32 fever postfix/smtps/smtpd[11711]: connect from localhost[127.0.0.1]
Dec  1 14:26:36 fever postfix/smtps/smtpd[11711]: SSL_accept error from localhost[127.0.0.1]: -1
Dec  1 14:26:36 fever postfix/smtps/smtpd[11711]: warning: TLS library problem: 11711:error:140760FC:SSL routines:SSL23_GET_CLIENT_HELLO:unknown protocol:s23_srvr.c:628:
Dec  1 14:26:36 fever postfix/smtps/smtpd[11711]: lost connection after CONNECT from localhost[127.0.0.1]
Dec  1 14:26:36 fever postfix/smtps/smtpd[11711]: disconnect from localhost[127.0.0.1]
Dec  1 14:34:25 fever dovecot: imap-login: Login: user=<wlee1970>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, mpid=11891, secured
Dec  1 14:34:25 fever dovecot: imap(wlee1970): Disconnected: Logged out bytes=79/681

[/HTML]


what do i need to do to get this fixed.

PS looking for Steps to clear this up.

Thanks
cid420

---

