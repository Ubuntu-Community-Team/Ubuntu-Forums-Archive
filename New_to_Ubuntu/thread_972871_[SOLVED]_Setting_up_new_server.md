---
title: "[SOLVED] Setting up new server"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by dipeshmehta on 2008-11-06
Hello,

%greetings;

I have recently received Ubuntu Server 8.04 CD.  I want to set it up for some 12-14 clients connected to it. I have Intel P-III / 256MB RAM / 40GB Hard Disk.  I want my server primary act as Mail Server which acts as internal mail server for clients in local network as well as it should communicate with my ISP provided external mailserver for sending and receiving mails from/to out of the world.

I am looking for step-by-step guide doing this. Can anybody please guide me? or please provide me link for the same.

Thanks in advance.

Dipesh

---

### Post by xnostradamusx on 2008-11-06
heres a guide for you

[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

good luck :guitar:

---

### Post by Mr_JMM on 2008-11-06
[https://help.ubuntu.com/8.04/serverguide/C/index.html]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by Mr_JMM on 2008-11-06
@ xnostradamusx:

That's a good find. Very impressive looking guide.

[D'oh, that should have been an edit. sorry]

---

### Post by xnostradamusx on 2008-11-06
> **Mr_JMM said:**
> @ xnostradamusx:

That's a good find. Very impressive looking guide.

[D'oh, that should have been an edit. sorry]

no problem i hope he finds it complete and useful

:guitar:

---

### Post by dipeshmehta on 2008-11-07
> **xnostradamusx said:**
> heres a guide for you

[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

good luck :guitar:


thanks, I have reviewed & studied thoroughly the guide and now I am going to install my server.

:popcorn:

---

### Post by mapes12 on 2008-11-07
Here's another good guide:

[http://www.aboutdebian.com/](http://www.aboutdebian.com/)

Uses Debian but should be good for Ubuntu as well.

---

### Post by dipeshmehta on 2008-11-08
> **xnostradamusx said:**
> heres a guide for you

[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

good luck :guitar:

Hello,

I have installed my ubuntu server and started configuration step-by-step as per suggested guide.

:confused:
I have been stucked at two places; please review and suggest where I am going wrong:

1. In postfix configuration...
[I]echo 'pwcheck_method: saslauthd' >> /etc/postfix/sasl/smtpd.conf
echo 'mech_list: plain login' >> /etc/postfix/sasl/smtpd.conf[/I]
gives me "Permission denied"

2. In postfix configuration ... continue
[I]To see if SMTP-AUTH and TLS work properly now run the following command: 
  telnet localhost 25
After you have established the connection to your Postfix mail server type 
  ehlo localhost
If you see the lines [/I]
I am not getting anything on my screen, as well as I cannot quit to the shell.

Thanks in advance.

---

### Post by cariboo on 2008-11-08
THe reason your command fialed is that you didn't run the commands as root. When configuring something like you are i usually use:

```
sudo -i
```

This runs you in an intercative shell that allows you to be root for as long as you need to with out having to enter sudo fo every command.

The reason the telnet session didn't work was your mail server wasn't running, and you hadn't finished configuring it yet.

Jim

---

### Post by hyper_ch on 2008-11-08
on a side-note: If you want to run your mailserver also as normal mailserver throgh the internet you will very likely need a static IP address. Most mailservers will not accept emails from a mailserver on a dynamic ip address.

---

### Post by dipeshmehta on 2008-11-08
> **cariboo907 said:**
> THe reason your command fialed is that you didn't run the commands as root. When configuring something like you are i usually use:

```
sudo -i
```

This runs you in an intercative shell that allows you to be root for as long as you need to with out having to enter sudo fo every command.

The reason the telnet session didn't work was your mail server wasn't running, and you hadn't finished configuring it yet.

Jim

Thanks, my first problem has been solved using "sudo -i" but I am still not able to telnet.  I have completely restarted the ubuntu server after finishing configuration as mentioned in guide.

---

### Post by hyper_ch on 2008-11-08
```

sudo apt-get install telnet

```

---

### Post by dipeshmehta on 2008-11-09
Hello,

I had followed the install instructions for the perfect hardy server

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I had issues with the mail portion, but I left it because it was of least importance to me at the time of installation. Now I have everything else done and would like to fix the mail portion of the server.

I get blocked after I set up postfix. There is a test :

telnet localhost 25

and then type

ehlo localhost

it says I am suppose to get

250-STARTTLS

and

250-AUTH LOGIN PLAIN 

but I am not getting anything on my screen, as well as I cannot quit to the shell.

My main.cf looks like this:
----------------------------------------
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
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = linserver.banlabs.in, localhost.banlabs.in, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks-reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

virtual_maps = hash:/etc/postfix/virtusertable

mydestination = /etc/postfix/local-host-names
------------------------------------
I found a silly mistake done by me, "smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks-reject_unauth_destination" should be "smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination"

Corrected and forking fine now.

Thanks to all for kind support.

Dipesh

---

