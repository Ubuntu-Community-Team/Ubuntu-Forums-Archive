---
title: "How can I send an email from the command line?"
date: 2008-02-29
forum: Programming Talk
---

### Post by davidtuti on 2008-02-29
Hi,

I' trying to cand execute a command in a shell-script to can send a email to somewhere out of my LAN.
I 've seen another post about that but he want to do with evolution. 
I don't have configured Evolution, could I do with other program? I've been reeding that I could do with mutt. But I think that I need install MTA like Sendmail. I 've installed sendmail but do I need configure?
What else I have to do it?

Any help?

Thanks a lot and sorry for my englsih

---

### Post by ruy_lopez on 2008-02-29
I used [this howto]("http://souptonuts.sourceforge.net/postfix_tutorial.html") to successfully send mail from the command line using postfix and a gmail account acting as a relay.

---

### Post by davidtuti on 2008-02-29
These is some dificult. I have to create certificate and more...

Do I have to do all these things to that I would like? I only want to can send mail from to oustide LAN from command line.


Thanks a lot,

---

### Post by Mr. C. on 2008-02-29
Gmail and other's won't allow you to send without authentication.

Here's a simpler way:

[http://gentoo-wiki.com/HOWTO_Gmail_and_sSMTP](http://gentoo-wiki.com/HOWTO_Gmail_and_sSMTP)

---

### Post by mssever on 2008-02-29
When I needed to do that, I just installed postfix and mailx. Then sending mail is as simple as ```
mail -s "some subject" recipient@email.com < message_body.txt
```If that doesn't work, run ```
sudo dpkg-reconfigure postfix
```

---

### Post by davidtuti on 2008-03-01
> **mssever said:**
> When I needed to do that, I just installed postfix and mailx. Then sending mail is as simple as ```
mail -s "some subject" recipient@email.com < message_body.txt
```If that doesn't work, run ```
sudo dpkg-reconfigure postfix
```

Hi, I've tryed this but the mail don't arrive to destination. I don't have to configure anithing of postfix??
Thanks

---

### Post by Mr. C. on 2008-03-01
Do you have postfix installed, or Sendmail (earlier you said: I 've installed sendmail)?

Look at, and show you /var/log/mail.log.

---

### Post by ghostdog74 on 2008-03-01
does you LAN have other email servers? you can configure the MTA in sendmail configuration file to point to your LAN email server. Look up the  sendmail documentation if in doubt. or see [here]("http://www.docs.hp.com/en/32650-90906/ch10s07.html") on how to configure smart relay

---

### Post by davidtuti on 2008-03-01
Hi

I don't have mail server in my lan
I have a pc with ubuntu and a DSL connection. 

I send a mail using:
mail -s "some subject" [email]davidtuti@gmail.com[/email] < message_body.txt

And the logs says me:

Mar  1 11:45:11 david-desktop postfix/master[6187]: daemon started -- version 2.4.5, configuration /etc/postfix
Mar  1 11:45:24 david-desktop postfix/pickup[6188]: B1C4EAC44D: uid=0 from=<root>
Mar  1 11:45:24 david-desktop postfix/cleanup[6194]: B1C4EAC44D: message-id=<20080301104524.B1C4EAC44D@david-desktop>
Mar  1 11:45:24 david-desktop postfix/qmgr[6189]: B1C4EAC44D: from=<root@gmail.com>, size=297, nrcpt=1 (queue active)
Mar  1 11:45:24 david-desktop postfix/local[6196]: B1C4EAC44D: to=<davidtuti@gmail.com>, relay=local, delay=0.05, delays=0.03/0.01/0/0.01, dsn=5.1.1, status=bounced (unknown user: "davidtuti")
Mar  1 11:45:24 david-desktop postfix/cleanup[6194]: BB053AC44E: message-id=<20080301104524.BB053AC44E@david-desktop>
Mar  1 11:45:24 david-desktop postfix/bounce[6197]: B1C4EAC44D: sender non-delivery notification: BB053AC44E
Mar  1 11:45:24 david-desktop postfix/qmgr[6189]: BB053AC44E: from=<>, size=1947, nrcpt=1 (queue active)
Mar  1 11:45:24 david-desktop postfix/qmgr[6189]: B1C4EAC44D: removed
Mar  1 11:45:24 david-desktop postfix/local[6196]: BB053AC44E: to=<david@gmail.com>, orig_to=<root@gmail.com>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Mar  1 11:45:24 david-desktop postfix/qmgr[6189]: BB053AC44E: removed

The email don't arrive, any help?

---

### Post by Mr. C. on 2008-03-01
The mail can't arrive, because it is bouncing due to misconfiguration.  Lets follow along:

... postfix/pickup[6188]: B1C4EAC44D: uid=0 from=<root>

Postfix receives the mail from sendmail

... postfix/cleanup[6194]: B1C4EAC44D: message-id=<20080301104524.B1C4EAC44D@david-desktop>

Postfix assigns a message-ID

... postfix/qmgr[6189]: B1C4EAC44D: from=<root@gmail.com>, size=297, nrcpt=1 (queue active)

Postfix accepts the message into the queue.  Notice the Envelope From is "root@gmail.com".  Your machine is named gmail.com, and this is incorrect.

... postfix/local[6196]: B1C4EAC44D: to=<davidtuti@gmail.com>, relay=local, delay=0.05, delays=0.03/0.01/0/0.01, dsn=5.1.1, status=bounced (unknown user: "davidtuti")

Postfix attempts to deliver the mail via the "local" mail delivery agent, but finds there is no such user "davidtuti".  This means you do not have a davidtuti user in /etc/passwd or a same named alias in /etc/postfix/aliases.  Since postfix is configured to be gmail.com, it considers this address local.

The messages below show that postfix creates a bounce message and delivers the bounce message to the local user [email]david@gmail.com[/email].

However, this is not a local user, and your machine is not gmail.com !  So you have some misconfigurations.

Mar 1 11:45:24 david-desktop postfix/cleanup[6194]: BB053AC44E: message-id=<20080301104524.BB053AC44E@david-desktop>
Mar 1 11:45:24 david-desktop postfix/bounce[6197]: B1C4EAC44D: sender non-delivery notification: BB053AC44E
Mar 1 11:45:24 david-desktop postfix/qmgr[6189]: BB053AC44E: from=<>, size=1947, nrcpt=1 (queue active)
Mar 1 11:45:24 david-desktop postfix/qmgr[6189]: B1C4EAC44D: removed
Mar 1 11:45:24 david-desktop postfix/local[6196]: BB053AC44E: to=<david@gmail.com>, orig_to=<root@gmail.com>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)

At this point, it is best to show output from:

```
postconf -n
```

We'll find that you have myhostname and mydomainname incorrectly configured as gmail.com.

---

### Post by davidtuti on 2008-03-01
root@david-desktop:/etc/postfix# postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = gmail.com, david-desktop, localhost.localdomain, localhost
myhostname = david-desktop
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = smtp.gmail.com:587
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes

Thansk for your help

---

### Post by Mr. C. on 2008-03-01
[QUOTE=davidtuti;4433306]root@david-desktop:/etc/postfix# postconf -n

```
mydestination = gmail.com, david-desktop, localhost.localdomain, localhost
```

You are not destination "gmail.com" !  In other words, your postfix installation does not handle email for gmail - it handles email for your own personal system or domain(s).  Remove gmail.com.

```
myhostname = david-desktop
```

The destination "david-desktop" is not fully qualified, and will cause various errors, including other server's rejecting your email.  This should be a fully qualfied hostname.  Change it to david-desktop.localdomain if you want.


```
relayhost = smtp.gmail.com:587
```

Ok, so you are trying to mail by relaying to Gmail.  Gmail requires TLS to be enabled first.  Let's see how I know that.

```

telnet smtp.gmail.com 587 
Trying 209.85.199.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP l17sm25523325rvb.21
EHLO example.com
250-mx.google.com at your service, [204.11.230.89]
250-SIZE 28311552
250-8BITMIME
[COLOR="Red"]250-STARTTLS[/COLOR]
250 ENHANCEDSTATUSCODES
```

This suggests that want require your system to negotiate a TLS session before they allow you to authenticate via SASL.

```
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
```

And from the rest of this we see no settings that will start TLS negotiation nor authentication.  So, follow along with this thread to get you the rest of the way (and follow links posted):

[http://ubuntuforums.org/showthread.php?t=706606&highlight=postfix+gmail](http://ubuntuforums.org/showthread.php?t=706606&highlight=postfix+gmail)

---

### Post by ruy_lopez on 2008-03-01
> **Mr. C. said:**
> 

```
myhostname = david-desktop
```

The destination "david-desktop" is not fully qualified, and will cause various errors, including other server's rejecting your email.  This should be a fully qualfied hostname.  Change it to david-desktop.localdomain if you want.


The myhostname is only part of the domain. The value in mydomain is appended to myhostname to create the FQDN. i.e. adding "home" to mydomain will send mail as david-desktop.home.

---

### Post by Mr. C. on 2008-03-01
There is no mydomain config var set in the OPs config, so it defaults to myhostname minus the first component.

And with append_dot_mydomain = no, the domain will not get tacked on for locally generated mail.

---

### Post by davidtuti on 2008-03-01
> **Mr. C. said:**
> [QUOTE=davidtuti;4433306]root@david-desktop:/etc/postfix# postconf -n

```
mydestination = gmail.com, david-desktop, localhost.localdomain, localhost
```

You are not destination "gmail.com" !  In other words, your postfix installation does not handle email for gmail - it handles email for your own personal system or domain(s).  Remove gmail.com.

```
myhostname = david-desktop
```

The destination "david-desktop" is not fully qualified, and will cause various errors, including other server's rejecting your email.  This should be a fully qualfied hostname.  Change it to david-desktop.localdomain if you want.


```
relayhost = smtp.gmail.com:587
```

Ok, so you are trying to mail by relaying to Gmail.  Gmail requires TLS to be enabled first.  Let's see how I know that.

```

telnet smtp.gmail.com 587 
Trying 209.85.199.111...
Connected to gmail-smtp.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP l17sm25523325rvb.21
EHLO example.com
250-mx.google.com at your service, [204.11.230.89]
250-SIZE 28311552
250-8BITMIME
[COLOR="Red"]250-STARTTLS[/COLOR]
250 ENHANCEDSTATUSCODES
```

This suggests that want require your system to negotiate a TLS session before they allow you to authenticate via SASL.

```
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes
```

And from the rest of this we see no settings that will start TLS negotiation nor authentication.  So, follow along with this thread to get you the rest of the way (and follow links posted):

[http://ubuntuforums.org/showthread.php?t=706606&highlight=postfix+gmail](http://ubuntuforums.org/showthread.php?t=706606&highlight=postfix+gmail)

Thanks

I did all the howto minus:

 cat /etc/ssl/certs/Thawte_Premium_Server_CA.pem >> cacert.pem 
cat: /etc/ssl/certs/Thawte_Premium_Server_CA.pem: No existe el fichero ó directorio
 
The file Thawte_Premium_Server_CA.pem doesn't exit. I've sent another mail and the log says me:

Mar  1 19:43:33 david-desktop postfix/postfix-script[6812]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Mar  1 19:43:33 david-desktop postfix/postfix-script[6835]: starting the Postfix mail system
Mar  1 19:43:33 david-desktop postfix/master[6836]: daemon started -- version 2.4.5, configuration /etc/postfix
Mar  1 19:48:25 david-desktop postfix/pickup[6837]: 7E791AC44F: uid=0 from=<root>
Mar  1 19:48:25 david-desktop postfix/cleanup[6948]: 7E791AC44F: message-id=<20080301184825.7E791AC44F@david-desktop>
Mar  1 19:48:25 david-desktop postfix/qmgr[6838]: 7E791AC44F: from=<root@gmail.com>, size=293, nrcpt=1 (queue active)
Mar  1 19:48:29 david-desktop postfix/smtp[6950]: 7E791AC44F: to=<davidtuti@gmail.com>, relay=smtp.gmail.com[216.239.59.109]:587, delay=4.2, delays=0.02/0.01/3.9/0.2, dsn=5.7.0, status=bounced (host smtp.gmail.com[216.239.59.109] said: 530 5.7.0 Must issue a STARTTLS command first u14sm10399872gvf.1 (in reply to MAIL FROM command))
Mar  1 19:48:29 david-desktop postfix/cleanup[6948]: D75D2AC450: message-id=<20080301184829.D75D2AC450@david-desktop>
Mar  1 19:48:29 david-desktop postfix/bounce[6951]: 7E791AC44F: sender non-delivery notification: D75D2AC450
Mar  1 19:48:29 david-desktop postfix/qmgr[6838]: D75D2AC450: from=<>, size=2138, nrcpt=1 (queue active)
Mar  1 19:48:29 david-desktop postfix/qmgr[6838]: 7E791AC44F: removed
Mar  1 19:48:31 david-desktop postfix/smtp[6950]: D75D2AC450: to=<root@gmail.com>, relay=smtp.gmail.com[216.239.59.109]:587, delay=1.3, delays=0/0/1.2/0.14, dsn=5.7.0, status=bounced (host smtp.gmail.com[216.239.59.109] said: 530 5.7.0 Must issue a STARTTLS command first g11sm10446219gve.6 (in reply to MAIL FROM command))
Mar  1 19:48:31 david-desktop postfix/qmgr[6838]: D75D2AC450: removed

Any help?

---

### Post by Mr. C. on 2008-03-01
This is why I deplore "How Tos", and rarely give pointers to them.  One step doesn't work, user's don't understand its purpose and decide to just skip the step as if it doesn't matter, and move on. 

You need a root CA bundle; you may have one on your system, but need to find it and configure postfix to use it.  It may be any of a variety of names, or be installed one or more times already by any number of packages.

I don't have a recommendation on where to find one, short of searching the forums here.  This is a critical security step; you need a *trusted, reliable* root CRT bundle, or at least one that includes the root CA that gmail uses.

Mar 1 19:43:33 david-desktop postfix/postfix-script[6812]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ

See why your resolv.conf files differ - postfix uses the chrooted one listed first, the rest of your system uses the second one.

It does not appear that your server is attempting to connect via TLS.  This means either/both of:
```

smtp_use_tls = yes
TLS support is not yet configured correctly
```

You can set smtp_tls_loglevel = 2

do get more debug info about what is happening with TLS.

---

### Post by davidtuti on 2008-03-01
Sorry,
Where I do put this parameter?

---

### Post by Mr. C. on 2008-03-01
main.cf - most every postfix parameter goes there.

---

### Post by davidtuti on 2008-03-01
more main.cf

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_tls_loglevel = 2

the log is:
Mar  1 22:02:29 david-desktop postfix/postfix-script[8207]: stopping the Postfix mail system
Mar  1 22:02:29 david-desktop postfix/master[6836]: terminating on signal 15
Mar  1 22:02:29 david-desktop postfix/postfix-script[8210]: waiting for the Postfix mail system to terminate
Mar  1 22:02:34 david-desktop postfix/postfix-script[8266]: warning: /var/spool/postfix/etc/resolv.conf and /etc/resolv.conf differ
Mar  1 22:02:34 david-desktop postfix/postfix-script[8289]: starting the Postfix mail system
Mar  1 22:02:34 david-desktop postfix/master[8290]: daemon started -- version 2.4.5, configuration /etc/postfix
Mar  1 22:03:08 david-desktop postfix/pickup[8291]: 7D330AC450: uid=0 from=<root>
Mar  1 22:03:08 david-desktop postfix/cleanup[8302]: 7D330AC450: message-id=<20080301210308.7D330AC450@david-desktop>
Mar  1 22:03:08 david-desktop postfix/qmgr[8292]: 7D330AC450: from=<root@gmail.com>, size=293, nrcpt=1 (queue active)
Mar  1 22:03:09 david-desktop postfix/smtp[8304]: 7D330AC450: to=<davidtuti@gmail.com>, relay=smtp.gmail.com[216.239.59.109]:587, delay=0.53, delays=0.03/0.01/0.42/0.08, dsn=5.7.0, status=bounced (host smtp.gmail.com[216.239.59.109] said: 530 5.7.0 Must issue a STARTTLS command first g9sm10549194gvc.4 (in reply to MAIL FROM command))
Mar  1 22:03:09 david-desktop postfix/cleanup[8302]: 1D9A2AC451: message-id=<20080301210309.1D9A2AC451@david-desktop>
Mar  1 22:03:09 david-desktop postfix/bounce[8305]: 7D330AC450: sender non-delivery notification: 1D9A2AC451
Mar  1 22:03:09 david-desktop postfix/qmgr[8292]: 1D9A2AC451: from=<>, size=2136, nrcpt=1 (queue active)
Mar  1 22:03:09 david-desktop postfix/qmgr[8292]: 7D330AC450: removed
Mar  1 22:03:09 david-desktop postfix/smtp[8304]: 1D9A2AC451: to=<root@gmail.com>, relay=smtp.gmail.com[216.239.59.109]:587, delay=0.45, delays=0.01/0/0.36/0.08, dsn=5.7.0, status=bounced (host smtp.gmail.com[216.239.59.109] said: 530 5.7.0 Must issue a STARTTLS command first q9sm10442170gve.10 (in reply to MAIL FROM command))
Mar  1 22:03:09 david-desktop postfix/qmgr[8292]: 1D9A2AC451: removed

---

### Post by mssever on 2008-03-01
I don't know a whole lot about Postfix configuration, but I have a working setup. I'm not trying to relay through Gmail or anything complicated like that. I just send directly, and it works. Here's my main.cf for reference (note that I have the top-level domain .mss configured by my local DNS; your setup will differ.):
```
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

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = scott-laptop.mss
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = scott-laptop.mss, localhost.mss, , localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
```
Here's my /etc/malname: ```
scott-laptop.mss
```
Of course, you'll need to make adjustments, since your machine doesn't have the same name as mine. :)

---

### Post by davidtuti on 2008-03-01
I've solved the other prolem and I have other:
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: certificate verification failed for smtp.gmail.com: num=20:unable to get local issuer certificate
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: verify return: 0
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: certificate verification failed for smtp.gmail.com: num=27:certificate not trusted
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: verify return: 0
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: certificate verification depth=0 subject=/C=US/ST=California/L=Mountain View/O=Google Inc/CN=smtp.gmail.com
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: certificate verification failed for smtp.gmail.com: num=21:unable to verify the first certificate
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: verify return: 0
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 read server certificate A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:error in SSLv3 read server key exchange A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:error in SSLv3 read server key exchange A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 read server done A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 write client key exchange A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 write change cipher spec A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 write finished A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 flush data
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:error in SSLv3 read finished A
Mar  2 02:39:21 david-desktop last message repeated 3 times
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: SSL_connect:SSLv3 read finished A
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: save session smtp:216.239.59.109:587:mx.google.com to smtp cache
Mar  2 02:39:21 david-desktop postfix/tlsmgr[6762]: put smtp session id=smtp:216.239.59.109:587:mx.google.com [data 997 bytes]
Mar  2 02:39:21 david-desktop postfix/tlsmgr[6762]: write smtp TLS cache entry smtp:216.239.59.109:587:mx.google.com: time=1204421961 [data 997 bytes]
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: Unverified: subject_CN=smtp.gmail.com, issuer=Thawte Premium Server CA
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: TLS connection established to smtp.gmail.com: TLSv1 with cipher DES-CBC3-SHA (168/168 bits)
Mar  2 02:39:21 david-desktop postfix/smtp[6761]: 7CF6CAC451: to=<root@gmail.com>, relay=smtp.gmail.com[216.239.59.109]:587, delay=1.1, delays=0.01/0/0.97/0.08, dsn=5.5.1, status=bounced (host smtp.gmail.com[216.239.59.109] said: 530 5.5.1 Authentication Required u14sm10765190gvf.1 (in reply to MAIL FROM command))
Mar  2 02:39:21 david-desktop postfix/qmgr[6755]: 7CF6CAC451: removed

---

### Post by davidtuti on 2008-03-01
I've reinsalled all again and I have another error:

root@david-desktop:/etc/postfix# postconf -n
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
disable_dns_lookups = yes
inet_interfaces = all
relayhost = [smtp.gmail.com]:587
smtp_generic_maps = hash:/etc/postfix/generic
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_tls_cert_file = /etc/postfix/FOO-cert.pem
smtp_tls_key_file = /etc/postfix/FOO-key.pem
smtp_tls_loglevel = 2
smtp_tls_per_site = hash:/etc/postfix/tls_per_site
smtp_tls_session_cache_database = btree:/var/run/smtp_tls_session_cache
smtp_use_tls = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = no
smtpd_sasl_local_domain = $myhostname
smtpd_tls_CAfile = /etc/postfix/cacert.pem
smtpd_tls_cert_file = /etc/postfix/FOO-cert.pem
smtpd_tls_key_file = /etc/postfix/FOO-key.pem
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:/var/run/smtpd_tls_session_cache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
transport_maps = hash:/etc/postfix/transport


The erro:

ar  2 05:32:14 david-desktop postfix/cleanup[14507]: EB6E628B44: message-id=<20080302043214.EB6E628B44@david-desktop.localdomain>
Mar  2 05:32:14 david-desktop postfix/qmgr[14499]: EB6E628B44: from=<root@david-desktop.localdomain>, size=342, nrcpt=1 (queue active)
Mar  2 05:32:14 david-desktop postfix/smtp[14509]: initializing the client-side TLS engine
Mar  2 05:32:14 david-desktop postfix/tlsmgr[14510]: open smtp TLS cache btree:/var/run/smtp_tls_session_cache
Mar  2 05:32:14 david-desktop postfix/tlsmgr[14510]: tlsmgr_cache_run_event: start TLS smtp session cache cleanup
Mar  2 05:32:14 david-desktop postfix/smtp[14509]: warning: relayhost configuration problem
Mar  2 05:32:15 david-desktop postfix/smtp[14509]: EB6E628B44: to=<davidtere22@hotmail.com>, relay=none, delay=0.05, delays=0.03/0.02/0/0, dsn=4.3.5, status=deferred (unable to look up host smtp.gmail.com: No address associated with hostname)

---

### Post by davidtuti on 2008-03-01
It's OKKKKKK

Well, when I reboot all problems dissapear.

I have to say that the link that I understand better and I think better is 
[http://www.luzblanco.com/ultimas/ubuntu-6.06-postfix-cuenta-gmail.html](http://www.luzblanco.com/ultimas/ubuntu-6.06-postfix-cuenta-gmail.html)

Thank you for all an especially for Mr. C.

:):):):):):):

---

