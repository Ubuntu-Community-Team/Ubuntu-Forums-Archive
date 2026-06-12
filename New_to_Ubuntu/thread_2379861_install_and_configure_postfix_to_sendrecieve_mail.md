---
title: "install and configure postfix to send/recieve mail"
date: 2017-12-10
forum: New to Ubuntu
---

### Post by micahpage on 2017-12-10
I cant for the life of me get postfix to work on ubuntu 14.04

I am going through this tutorial
[https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04)

and when i run 
```
echo "This is the body of the email" | mail -s "This is the subject line" metulburr


```
I get a Maildir file in my home, but nothing is in it. Its not a directory at all. I dont get anything in /var/mail/metulburr either. 

This is a portion of my main.cf
```
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for# information on enabling SSL in the smtp client.


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = python-forum
#alias_maps = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
#mydestination = python-gaming.com, python-gaming, localhost.localdomain, localhost
mydestination = python-forum.io, python-forum
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
#inet_interfaces = localhost
#inet_interfaces = 127.0.0.1
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/



```

```
metulburr ~ $ sudo service postfix restart * Stopping Postfix Mail Transport Agent postfix                                                  [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                                                  [ OK ] 
metulburr ~ $ echo "This is the body of the email" | mail -s "This is the subject line" metulburr
metulburr ~ $ cat Maildir 
metulburr ~ $ ls -l
total 4
-rw------- 1 metulburr metulburr   0 Dec 10 20:15 Maildir



```

---

### Post by micahpage on 2017-12-10
EDIT:
Ok i deleted the Maildir file and redid it and it worked. However i cant send mail actually out. So for example if i try to send a mail to my gmail i get this in Maildir/new

```
metulburr ~ $ mail"/home/metulburr/Maildir": 2 messages 2 new
>N   1 Mail Delivery Syst                   79/3047  Undelivered Mail Returned to Sender
 N   2 Mail Delivery Syst                   79/3063  Undelivered Mail Returned to Sender
? 1
Return-Path: <>
X-Original-To: metulburr@python-forum
Delivered-To: metulburr@python-forum
Received: by python-forum (Postfix)
	id 658DF1408DD; Sun, 10 Dec 2017 20:41:17 -0500 (EST)
Date: Sun, 10 Dec 2017 20:41:17 -0500 (EST)
From: MAILER-DAEMON@python-forum.io (Mail Delivery System)
Subject: Undelivered Mail Returned to Sender
To: metulburr@python-forum
Auto-Submitted: auto-replied
MIME-Version: 1.0
Content-Type: multipart/report; report-type=delivery-status;
	boundary="B63CC1408DC.1512956477/python-forum"
Message-Id: <20171211014117.658DF1408DD@python-forum>


This is a MIME-encapsulated message.


--B63CC1408DC.1512956477/python-forum
Content-Description: Notification
Content-Type: text/plain; charset=us-ascii


This is the mail system at host python-forum.


I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.


For further assistance, please send mail to postmaster.


If you do so, please include this problem report. You can
delete your own text from the attached returned message.


                   The mail system


<metulburr@gmail.com>: host gmail-smtp-in.l.google.com[74.125.124.26] said:
    550-5.7.1 [IP_ADDRESS_REMOVED       1] Our system has detected an unusual rate
    of 550-5.7.1 unsolicited mail originating from your IP address. To protect
    our 550-5.7.1 users from spam, mail sent from your IP address has been
    blocked. 550-5.7.1 Please visit 550-5.7.1
    https://support.google.com/mail/?p=UnsolicitedIPError to review our 550
    5.7.1 Bulk Email Senders Guidelines. i33si389378iod.312 - gsmtp (in reply
    to end of DATA command)


--B63CC1408DC.1512956477/python-forum
Content-Description: Delivery report
Content-Type: message/delivery-status


Reporting-MTA: dns; python-forum
X-Postfix-Queue-ID: B63CC1408DC
X-Postfix-Sender: rfc822; metulburr@python-forum
Arrival-Date: Sun, 10 Dec 2017 20:41:16 -0500 (EST)


Final-Recipient: rfc822; PERSONAL_GMAIL_REMOVED
Action: failed
Status: 5.7.1
Remote-MTA: dns; gmail-smtp-in.l.google.com
Diagnostic-Code: smtp; 550-5.7.1 [198.199.80.192       1] Our system has
    detected an unusual rate of 550-5.7.1 unsolicited mail originating from
    your IP address. To protect our 550-5.7.1 users from spam, mail sent from
    your IP address has been blocked. 550-5.7.1 Please visit 550-5.7.1



```

---

