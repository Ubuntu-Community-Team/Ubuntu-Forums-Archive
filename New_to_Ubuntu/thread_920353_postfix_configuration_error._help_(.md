---
title: "postfix configuration error. help :("
date: 2008-09-15
forum: New to Ubuntu
---

### Post by ams11 on 2008-09-15
this is my **main.cf** configuration for postfix

[I]
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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = enyo.venom.lab
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydomain = venom.lab
myorigin = $mydomain
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
mynetworks_style = subnet
mynetworks = 10.3.1.0/24, 10.3.2.0/24, 127.0.0.0/8
#relay_domains = $mydestination
#relayhost = $mydomain
 
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = 
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authentication,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
#relay_recipient_maps = hash:/etc/postfix/relay_recipients
#local_recipient_maps = 

[/I]

my mail server ip address = 10.3.1.4 and my client machine is 10.3.2.3

i also use dovecot-imap with mbox mail box

on client, i created a user "ams" and use mutt to send/receive email.

i cant never find the emails i sent, eventho it says mail sent.

**/var/log/mail.log**

[I]
Sep 15 11:18:29 enyo dovecot: imap-login: Login: user=<ams>, method=PLAIN, rip=10.3.2.3, lip=10.3.1.4, TLS
Sep 15 11:18:45 enyo postfix/smtpd[4544]: connect from unknown[10.3.2.3]
Sep 15 11:18:45 enyo postfix/smtpd[4544]: warning: unknown smtpd restriction: "permit_sasl_authentication"
Sep 15 11:18:45 enyo postfix/smtpd[4544]: NOQUEUE: reject: RCPT from unknown[10.3.2.3]: 451 4.3.5 Server configuration error; from=<ams@venom.lab> to=<ams@venom.lab> proto=ESMTP helo=<client1.venom.lab>
Sep 15 11:18:45 enyo postfix/cleanup[4547]: 7CEC57E4B: message-id=<20080915111845.7CEC57E4B@enyo.venom.lab>
Sep 15 11:18:45 enyo postfix/qmgr[4397]: 7CEC57E4B: from=<double-bounce@enyo.venom.lab>, size=989, nrcpt=1 (queue active)
Sep 15 11:18:45 enyo postfix/smtpd[4544]: disconnect from unknown[10.3.2.3]
Sep 15 11:18:45 enyo postfix/local[4548]: 7CEC57E4B: to=<root@venom.lab>, orig_to=<postmaster>, relay=local, delay=0.11, delays=0.07/0/0/0.04, dsn=2.0.0, status=sent (delivered to mailbox)
Sep 15 11:18:45 enyo postfix/qmgr[4397]: 7CEC57E4B: removed

[/I]

i tried to telnet from client machine to the mail server, and i got this output:
[B]
telnet enyo.venom.lab 25
Trying 10.3.1.4...
Connected to enyo.venom.lab.
Escape character is '^]'.
220 enyo.venom.lab ESMTP Postfix (Ubuntu)
ehlo venom.lab
250-enyo.venom.lab
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN
250-AUTH=PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
mail from:ams@venom.lab
250 2.1.0 Ok
rcpt to:ams@venom.lab
451 4.3.5 Server configuration error

[/B]

i am a newbie in ubuntu 
any help would be greatly appreciated 

thank you

---

