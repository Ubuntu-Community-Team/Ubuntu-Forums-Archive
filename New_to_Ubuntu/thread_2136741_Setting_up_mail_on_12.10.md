---
title: "Setting up mail on 12.10"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by bullet333 on 2013-04-18
**EDIT:**
I believe I've setup sendmail, but still having issues sending mail automatically. 
 Well I figured out that Webmin has a Sendmail and Read User Mail modules. I've been messing around with those and was able to send mail to my exchange server manually, but for some reason logrotate cannot send mail properly. It produces the following errors:

> [COLOR=#333333]/etc/cron.daily/logrotate:[/COLOR]
mail: cannot send message: Process exited with a non-zero statuserror: mail command failed for /var/tmp/syslog.1run-parts: /etc/cron.daily/logrotate exited with return code 1/etc/cron.daily/sarg: [COLOR=#333333]SARG: Period covered by log files: 02/05/2013-02/05/2013[/COLOR]

> [COLOR=#333333]The original message was received at Fri, 3 May 2013 07:46:27 -0400[/COLOR]
from root@localhost ----- The following addresses had permanent fatal errors -----<[FONT=Verdana]myemail@domain.com[/FONT]> (reason: 550 5.1.1 <myemail@domain.com>... User unknown) (expanded from: <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>)[/FONT]
----- Transcript of session follows -----... while talking to [127.0.0.1]:>>> DATA<<< 550 5.1.1 <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>... User unknown[/FONT]
550 5.1.1 <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>... User unknown [/FONT][COLOR=#333333]<<< 503 5.0.0 Need RCPT (recipient)[/COLOR]

Although what's strange is that I can forward the error messages manually and they work fine!

-------------------------------------------------------------------------------------------------------------------------------------------------
[B]OLD OP:
[/B]
I'm trying to figure out how to setup a very simple mail service using the command line and can't seem to find any help using Google (everyone wants to use SendMail or MailX). I have a script that will mail my work email if the disk usage is at a certain point using the 'mail' command.  So I'm trying to setup the 'mail' service.

The script is saved within cron.hourly as spacecheck.sh
```
  
GNU nano 2.2.6              File: /etc/cron.hourly/spacecheck.sh

#!/bin/bash
CURRENT=$(df / | grep / | /dev/sda1 '{ print $5}' | sed 's/%//g')
THRESHOLD=30


if [ "$CURRENT" -gt "$THRESHOLD" ] ; then
    mail -s 'Disk Space Alert' user@domain.com << EOF
Your root partition remaining free space is critically low. Used: $CURRENT%
EOF
fi

```

But I don't think the problem is with my script as I'm just trying to test it out.  I've already installed the Mail service using apt-get install mail, but I don't know if there's any configuration as 'man' or online guides aren't helping.

When I attempt to perform the following command:
```
mail <user>@gmail.com
```

I fill in the information and hit Ctrl + D, I get the following error:
```
cannot send message: Process exited with a non-zero status
```

When I just type in 'mail' it says 'No mail for root'.

I don't need a fancy GUI email program because I'm just using SSL connection in terminal.  I don't need to receive email or check my emails.  This Ubuntu machine is setup as a proxy server and that's it.

---

### Post by Cheesemill on 2013-04-18
If you have a Gmail account you can use for sending the mail from then you can use this tutorial....

[http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp](http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp)

---

### Post by bullet333 on 2013-04-18
Thanks, I tried setting up ssmtp but I was wondering if I could use a different domain, such as my exchange server?

I didn't want to use my personal gmail account for the company especially since my password is in written within the config.  I suppose I could just create a fake gmail account just for that purpose.  Although if I use the ssmtp would I have to alter my script for crontab?  i.e. instead of using [COLOR=#000000][FONT=Ubuntu Mono]mail -s 'Disk Space Alert' [email]user@domain.com[/email][/FONT][/COLOR] [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR] [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR] use [COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR][FONT=Ubuntu Mono]ssmtp [email]recepient_name@gmail.com[/email][/FONT]&#8203; ?[FONT=Ubuntu Mono][/FONT]

---

### Post by Cheesemill on 2013-04-18
If you have an exchange server then it's pretty easy to set up, just do a ....
```
sudo apt-get install postfix
```
And then on the configuration screen select 'Satellite system' and then enter your domain (example.com) and either the FQDN or IP address of your exchange server.

If your exchange server is set up to allow SMTP connections from your network then you should be good to go.

---

### Post by bullet333 on 2013-04-18
Ok I installed and set that up.  Is there a way to change the configuration in case I messed something up?  Should I be using 'sendmail' or the 'mail' command(s) and how do I use them properly? 

I have a firewall that only allows traffic from our email filter as well via a specific IP and port so I'll probably have to allow mail from this server as well.

EDIT:
I believe I found the config file located in /etc/postfix/main.cf, so that answers my first question.

The config is setup as follows:
```

myhostname = Squid
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = <domain>.local, Squid, localhost.localdomain, localhost
relayhost = <server>.<domain>.local
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = loopback-only

```
*[SIZE=1]<domain> and <server> are commented out[/SIZE]*

I'm a little confused as to what the domain names are supposed to be set as.  Should it be the same as the domain for my email, i.e. [EMAIL="user@domain.com"]user@domain.com[/EMAIL], or would it be the domain of my network?

Should I also alter the /etc/aliases folder to add my exchange user?

```
# See man 5 aliases for formatpostmaster:    root

```

The reason I'm asking all this is because trying to send a message from the terminal using either 'sendmail' or 'mail' doesn't seem to work although it doesn't error out.  Makes me think nothing is wrong with my ubuntu configs but rather my firewall blocking them.  That makes me wonder how the email gets sent?  Does it go through the internet or directly from exchange?

---

### Post by bullet333 on 2013-04-19
I'm still having trouble setting this up and getting it to work with my Exchange Server.  All I want to do is to be able to send a quick email from my Ubuntu machine to my Exchange account.

I found this guide and pretty much completed all the tasks except for receiving the sent mail:
[http://www.fritzmahnke.com/2010/12/25/use-postfix-to-send-email-through-microsoft-exchange-server/](http://www.fritzmahnke.com/2010/12/25/use-postfix-to-send-email-through-microsoft-exchange-server/)

I was able to send myself a message using the telnet 'MAIL FROM/RCPT' commands, but still cannot figure out how to get sendmail to work considering it doesn't even error out!

Someone please help me!

EDIT:
So I found the mail log in /var/tmp/mail.log.1

```

Apr 19 07:27:19 Squid postfix/qmgr[56581]: 49E8884447: from=<bullet@Squid>, size=314, nrcpt=1 (queue active)
Apr 19 07:27:19 Squid postfix/smtp[61502]: warning: relayhost configuration problem
Apr 19 07:27:19 Squid postfix/smtp[61502]: 49E8884447: to=<me@gmail.com>, relay=none, delay=50841, delays=50841/0.04/0/0, dsn=4.3.5, status=deferred (Host or domain name not found. Name service error for name=server.domain.loc

```
[I][SIZE=1]I edited out the server/domain information that I do not want to share on the internet
[/SIZE][/I]
It appears that some of my configurations are incorrect for the 'relayhost'. as I'm not exactly sure what that's supposed to be.  It's currently setup as 'mail.domain.com' (Host Record for my Exchange server).

---

### Post by bullet333 on 2013-05-03
Well I figured out that Webmin has a Sendmail and Read User Mail modules.  I've been messing around with those and was able to send mail to my exchange server manually, but for some reason logrotate cannot send mail properly.  It produces the following errors:

> [COLOR=#333333]/etc/cron.daily/logrotate:[/COLOR]
mail: cannot send message: Process exited with a non-zero statuserror: mail command failed for /var/tmp/syslog.1run-parts: /etc/cron.daily/logrotate exited with return code 1/etc/cron.daily/sarg: [COLOR=#333333]SARG: Period covered by log files: 02/05/2013-02/05/2013[/COLOR]

> [COLOR=#333333]The original message was received at Fri, 3 May 2013 07:46:27 -0400[/COLOR]
from root@localhost   ----- The following addresses had permanent fatal errors -----<[FONT=Verdana]myemail@domain.com[/FONT]>    (reason: 550 5.1.1 <myemail@domain.com>... User unknown)    (expanded from: <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>)[/FONT]
   ----- Transcript of session follows -----... while talking to [127.0.0.1]:>>> DATA<<< 550 5.1.1 <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>... User unknown[/FONT]
550 5.1.1 <[FONT=Verdana]myemail@domain.com[/FONT][FONT=Verdana]>... User unknown [/FONT][COLOR=#333333]<<< 503 5.0.0 Need RCPT (recipient)[/COLOR]

Although what's strange is that I can forward the error messages manually and they work fine!

---

