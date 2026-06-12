---
title: "Postfix+Dovecot issue"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Hiltsu on 2011-11-12
Hello there,

I needed to make e-mail server from scratch, but I am stuck with Dovecot. It seems that it is not able to create auth-pipe no matter what I do (I have tried for 2 days with all possible configuration scenarios). 

Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

1. File auth or auth-client at /var/spool/postfix/private never created.

2. **Error /var/log/mail.log**

Nov 12 12:39:29 posti postfix/smtpd[4957]: warning: SASL: Connect to private/auth failed: No such file or directory
Nov 12 12:39:29 posti postfix/smtpd[4957]: fatal: no SASL authentication mechanisms
Nov 12 12:39:30 posti postfix/master[4941]: warning: process /usr/lib/postfix/smtpd pid 4957 exit status 1
Nov 12 12:39:30 posti postfix/master[4941]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling

What I am seeing is that Dovecot is not crating the auth-file to /var/spool/postfix/private. I got it working once by using path /run/dovecot/auth-client at Postfix's main.cf, but after reboot I am back in original state. Dovecot is badly documented, because dovecot in this version uses auth.d and conf.d directives, and there is no way to test Dovecot's operation from command line (or if there is, I do not know how).

Essential config files are at this  moment:

*/etc/dovecot/auth.d# more 01-mail-stack-delivery.auth*
auth default {
socket listen {
client {
path = /var/spool/postfix/private/auth
mode = 0660
user = postfix
group = postfix
}
mechanisms = plain login
user=root
}}

3. *Postfix main.cf*

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no
mydomain = xxx.fi

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = po.xx.xx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = x.xx.fi, mailsrv.xx.local, localhost
relayhost = [mail.xx.fi]
mynetworks = 127.0.0.0/8 192.168.68.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
content_filter = smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_reci
pient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authentic
ated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -m "${EXTENSION}"
smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes
smtpd_sasl_auth_enable = yes
queue_directory = /var/spool/postfix
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtp_use_tls = yes
smtpd_tls_received_header = yes
#smtpd_tls_mandatory_protocols = SSLv3, TLSv1
#smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = no
tls_random_source = dev:/dev/urandom
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_timeout = 3600s
strict_rfc821_envelopes = yes

4. *master.cf snip*

# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd

.
.
.
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

I need either help how to debug Dovecot+Postfix or solution to this problem. I have tried all google'd solution (mostly to old Dovecot version) possible without luck. And why Dovecot is not creating pipe-file (auth or auth-client).

---

### Post by Hiltsu on 2011-11-12
Never mind .. thank God I am running these installations on Virtual server... easier to do "rollbacks". 

I decided to stop playing with 11.x verison and installed 10.x LTS. I followed partly this []("http://chiralsoftware.com/linux-system-administration/ubuntu-postfix-imap-dovecot-setup.seam") documentation and got it working - finally.

---

