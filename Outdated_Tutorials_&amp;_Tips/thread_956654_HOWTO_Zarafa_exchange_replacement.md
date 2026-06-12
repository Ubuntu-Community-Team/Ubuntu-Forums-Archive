---
title: "HOWTO: Zarafa exchange replacement"
date: 2008-10-23
forum: Outdated Tutorials &amp; Tips
---

### Post by E-Jey on 2008-10-23
**[SIZE="4"]Zarafa exchange replacement[/SIZE] **

For a long time I’m searching for a free exchange that runs on Ubuntu. Zimbra is very nice but you can’t connect with outlook for free. OpenExchange has the same issue and OpenChange is far from finished. I came across this news [message]("http://www.linuxelectrons.com/news/application/16997/microsoft-exchange-replacement-releases-code-under-gplv3"). 

Zarafa is licenced under the AGPL

Zarafa is a Mail Delivery Agent that supports: 
[LIST]
[*]AJAX webaccess with mail, contacts, todo, calendar
[*]POP,IMAP support
[*]Z-Push  (ActiveSync replacement, I use this with my iphone)
[*]3 outlook users (via a closed source component) 
[*]iCal support
[*]LDAP support (Active Directory)
[/LIST]

You can use Postfix and other MTA’s to send and receive mails. 
This tutorial describes how you can configure Zarafa. I use this for all my mail and it works perfect (also on my iPhone).

The webmail demo: [http://demo.zarafa.com/](http://demo.zarafa.com/)


**Step 1: install Zarafa**
install depedencies:

> apt-get install mysql-server-5.0 libmysqlclient15off apache2-mpm-prefork libapache2-mod-php5

Zarafa use Mysql as a storage backend. You need apache if you want to use the WebAccess and Z-Push, both are written in PHP. 

Download zarafa community edition, the download page is a little bit annoying because there is no direct download link. With lynx you can download it very easy. If you don’t have lynx: apt-get install lynx

> lynx [http://zarafa.com/?q=en/download-community](http://zarafa.com/?q=en/download-community)

Next we need to untar it: 

> tar zxvf zarafa-6.20-ubuntu8.04-i386.tar.gz
cd zarafa-6.20-ubuntu8.04-i386

Start the installer: 
> ./install.sh

Follow the steps on the screen. Don’t enter a serial number. You can enter all questions except of the MySQL password. 
Next we need to change a configuration in php.ini: 
> nano  /etc/php5/apache2/php.ini
Find with ctrl-w the line “magic_quotes_gpc = On” and turn On in Off. 
Restart apache:

> apache2ctl restart

Zarafa needs some older versions of some packages. Therefore you need to hold back some new packages otherwise zarafa will be removed when you run "apt-get dist-upgrade"

> echo libvmime0 hold | dpkg --set-selections
echo libical0 hold | dpkg --set-selections

Done, zarafa is installed! Time to add a user. 

> zarafa-admin -c jan -p secret -e [email]jan@debaas.nl[/email] -f “Jan Peter Balkenende” -a 0

-c = create user
-p = password
-e = email
-f = full name
-a = administrator 1 or 0 (true of false) 

To test Zarafa Webaccess, check with ifconfig the ip address and go this url: 

https://<ip>/webaccess

Works great isn’t it? Pop, imap, mapi etc everything is working..

**Step 3: install postfix and get mail working)**

Install postfix: 
> apt-get install postfix

Click oke and choose “No Configuration”

Next we have to change the config files. The fastest way is to copy these config files:

master.cf
> 
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
zarafa unix - n n - 10 pipe flags= user=vmail argv=/usr/bin/zarafa-dagent ${user}


#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


main.cf

> 
 See /usr/share/postfix/main.cf.dist for a commented, more complete version

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

mailbox_transport = zarafa: zarafa_destination_recipient_limit = 1

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = 
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, $mydomain
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = ipv4



Finally you have to add your hostname at this line: "myhostname = "

add the user vmail: 
> useradd vmail

Now you can send mail. To receive mail you have to configure the MX records for your domain and point them to your IP. 

Everything is working right now. 

**Step 4: run as non-root user (optional)**
This step is very recommended, but not necessary to get zarafa working. 

Add a user: 
> 
addgroup --system zarafa
adduser --system –-home /dev/null –-no-create-home –-ingroup zarafa –-disabled-password --gecos 'Zarafa services' --shell /bin/false zarafa

mkdir /var/log/zarafa

chown zarafa.zarafa /var/log/zarafa


You can change the config files of every zarafa service in /etc/zarafa. Open them all and edit the run_as_user and run_as_group options in zarafa. 

When you change the user of zarafa-licenced you can't use Outlook anymore. This is some annoying bug. A work around is to change some permissions: 

> chown zarafa.zarafa /var/run/zarafa-licensed
chown -R zarafa.zarafa  /var/lib/zarafa/


But when you restart zarafa licenced with /etc/init.d/zarafa-licenced restart you have to change the permissions of /var/run/zarafa-licenced again. You can solve this by adding the chown command to the init script. 

**Step 5: get Z-push working (optional)**

download Z-Push 
> wget [http://download.berlios.de/z-push/z-push-1.1.1.tar.gz](http://download.berlios.de/z-push/z-push-1.1.1.tar.gz)

untar to the apache directory
> tar zxvf z-push-<version>.tgz -C /var/www

Change some permissions:
> 
chmod 755 /var/www/z-push/state
chown www-data.www-data /var/www/z-push/state


Add an alias to the apache config.

/etc/apache2/sites-availiable/default
> Alias /Microsoft-Server-ActiveSync /var/www/z-push/index.php

*WARNING* You CANNOT simply rename the Z-Push directory to Microsoft-Server-ActiveSync.
This will cause Apache to send redirects to the PDA, which will definitely break your PDA
synchronisation.

Done

**More information**
[http://www.zarafa.nl/?q=en/content/documentation](http://www.zarafa.nl/?q=en/content/documentation)

---

### Post by PeterEs on 2008-10-26
Is there any posibility to use it for more then three outlook users? It looks very nice, but this is a big disadvantage for me.

---

### Post by sverre76 on 2008-11-04
> **PeterEs said:**
> Is there any posibility to use it for more then three outlook users? It looks very nice, but this is a big disadvantage for me.

They do have three other versions beside the community version. All of them seems to support unlimited Outlook accounts

[http://www.zarafa.com/?q=en/content/versions]("http://www.zarafa.com/?q=en/content/versions")

---

### Post by E-Jey on 2008-11-08
That's correct, you have to pay for more outlook users. You can also use imap for outlook if calender en contacts are not necessary. 

There is a new version of zarafa, I try to update this tutorial as fast as possible. I also want to add a anti spam/virus section.

---

### Post by mattbourne on 2008-11-15
Hi,

Thanks for putting up this tutorial; i have been trying to get zarafa working myself for a few weeks now.

I have just done a fresh install of ubuntu 32bit 8.04 and selected the LAMP option, from there i have followed your instructions but have come across some problems.

Firstly, postfix was not picking up mails from my backup MX server, the postfix error log has the following message:
-------------------
Nov 15 14:15:52 [my server name] postfix/master[8032]: fatal: /etc/postfix/master.cf: line 43: bad transport type: smtp_fallback_relay=
-------------------
i tried writing the name of an smtp server in here so the line looked like "smtp_fallback_relay=smtp.isp.com" but this didnt work.  I then commented out that line and got this error message:
-------------------
Nov 15 17:36:21 [my server name] postfix/master[4784]: fatal: /etc/postfix/master.cf: line 70: bad transport type: user=vmail
-------------------

Is anyone able to help me with these problems?

In the past I have selected Internet Site configuration when installing postfix - this is the first time I chose No Configuration and the first time I have had these errors.

The place I have stumbled previously is postfix has picked up the email, it is sat in the directory /var/mail but Zarafa will not pick it up from there to distribute to a user.

Any help would be much appreciated.

Thanks.

matt

---

### Post by mattbourne on 2008-11-15
ok, i have made a little progress this evening.

From reading this link... [http://zarafa.com/wiki/index.php/MTA_integration](http://zarafa.com/wiki/index.php/MTA_integration) I found i needed to add in "local_admin_users = root vmail" to the /etc/zarafa/server.cfg file.  That has stopped my last error message I posted.

I now have a new one of
----------------------------------------
Nov 15 21:06:48 [my server name] postfix/postfix-script[4901]: fatal: the Postfix mail system is not running
----------------------------------------

I have tried looking on the net this evening for help with sorting this one by I have had no luck :(

Any ideas???


Many thanks.

matt

---

### Post by w00ter on 2008-11-18
> **mattbourne said:**
> 
----------------------------------------
Nov 15 21:06:48 [my server name] postfix/postfix-script[4901]: fatal: the Postfix mail system is not running
----------------------------------------

I have tried looking on the net this evening for help with sorting this one by I have had no luck :(

Any ideas???


Many thanks.

matt
Hi Matt,

I have the EXACT same problem here.. although I am running Ubuntu server 8.10.. but should not make a difference.. :confused:

Anyone got Zarafa working? I'd love to get this thing running! 

Thanks !

---

### Post by mattbourne on 2008-11-18
Ive had no luck yet progressing past the error.  I have created a new thread on the Zarafa forum too but havent had any luck there but they had asked me for more detail...

[http://forums.zarafa.com/viewtopic.php?f=9&t=1354&sid=619a8e587137cc03693799f6941c2e24](http://forums.zarafa.com/viewtopic.php?f=9&t=1354&sid=619a8e587137cc03693799f6941c2e24)

matt

---

### Post by w00ter on 2008-11-19
Thanks for your reply Matt.. I'll keep an eye on the Zarafa topic as well, and maybe I can add some useful information. 

I was thinking of getting rid of postfix and try something like sendmail and fetchmail.. if I finaly get things running, I'll let you know right away. 

In the meantime, I'm hoping someone will provide us with a better fix ;)

---

### Post by mattbourne on 2008-11-19
w00ter,

Ive got it working.  Seeing as the Zarafa people were sooooo helpful, i thought i would post it here!!!

In your main.cf, insert the following line of code:
--------
mailbox_command = /usr/bin/zarafa-dagent "$USER"
--------

Dont have these 2 in there, delete them if they are:
--------
mailbox_transport = zarafa:
zarafa_destination_recipient_limit = 1
--------

You dont need to make any changes to master.cf so remove these if you have added them:
--------
zarafa unix - n n - 10 pipe
flags= user=vmail argv=/usr/bin/zarafa-dagent ${user}
--------

and remove the "vmail" user from this line in /etc/zarafa/server.cfg
--------
local_admin_users = root vmail
--------

I hope that works for you, i just need to sort out my emails going through my ISP's SMTP server until I can sort out a static IP address now (i think and hope!!!!)

Let me know how you get on.

matt

---

### Post by mattbourne on 2008-11-19
oh, forgot to say; this relies on you creating the users within ubuntu, e.g. "adduser fred" and within zarafa and whatever the username is, that is also email address, e.g. [email]fred@wilma.com[/email]

---

### Post by Twizzle on 2008-11-19
Thanks for the guide. I have managed to get this up and running on my home server which is great. I do have a couple of questions if you can help:

1) I can't seem to see how to sync my contacts with my email program on my desktop (Thunderbird or Evolution), I have managed to setup the calender and email but contacts are causing me more of a headache. Can you suggest a way to do this (if necessary with a different mail client)?

2) I can't seem to get my Nokia N95 to sync using Nokia Mail For Exchange (which is one of the reasons I went for Zarafa). When I do try to sync I get an "Error in exchange server. Try again later" error.  If I look at the log I get a "HTTP error code =500" entry. Could it be something to do with:

> Add an alias to the apache config.

/etc/apache2/sites-availiable/default

as I saw some guides that said I have to be careful where I put the line in the config file.... but not where I should! (I am just putting it at the top?)

Thanks again.

---

### Post by w00ter on 2008-11-20
Matt! 

It's good to hear you got it running! I've been messing around with my install so much that I need to reinstall Ubuntu Server :confused:

Since I work remotely I cant do that right now, but I'll do it soon and definatly try out your fix!

I'll let you know when I get things up and running again! 
And thanks again for taking the time to post your solution! 

Cheers!

ps. Twizzle, sorry I cant help you out with your 2 questions at this time.. perhaps I'll be of any help later on.

---

### Post by mattbourne on 2008-11-20
w00ter,

i am currently working on a little crib-sheet for myself for when i need to rebuild the server next time.  Once i have finished it, i will post it here as an alertnative to that at the start of this thread.

Twizzle - im afraid i havent got as far as contacts yet; im just pleased ive got zarafa working and it pushing mail through to my iPhone!!!

matt

---

### Post by Twizzle on 2008-11-20
Well I manager to get my Nokia to sync ok. I did some digging on the Z Push forum and found that i needed to:

```
apt-get install php-pear
```

and then:

```
 pear install mail
```

restart apache and bobs your uncle as they say - :)

So far I can sync Thunderbird and Lightning with my server and my N95 with my server. My only snag is contacts but I am still looking into it..

(I also need to work out how to retrieve emails from a pop3 ISP server onto my sever so I can view them through Zarafa... any ideas?)

---

### Post by mattbourne on 2008-11-20
i had that problem yesterday and probably found the same post!!!

I have tried playing with contacts this evening and they work fine for me.  do you need to turn the sync'ing on on an n95??

I am also looking at picking up pop3 email.  i found something but i didnt understand it.  Would you please let me know if you find out how to do it.

cheers.

matt

---

### Post by Twizzle on 2008-11-20
I have now installed getmail and if I run:

```
 getmail_fetch --delete --timeout=30 mailserver user password '| /usr/bin/zarafa-dagent -s user'
```

the email is downloaded from my ISP and I can read it in Zarafa. From [this]("http://www.howtoforge.com/debian_etch_getmail") post I think I can do a bit more tweaking and get it to run as a cron job every 5 mins or so. I did try to setup the getmailrc file but it kept telling me that it could not find the user name I was using... Ill keep trying.

I have not tried sending mail yet but I am sure that will be ok :)

---

### Post by mattbourne on 2008-11-20
that is the same post i found :).  where you have:
"... /usr/bin/zarafa-dagent -s user" would you replace the word user with the account in zarafa that you want the mail sent to??

---

### Post by Twizzle on 2008-11-21
Matt

Yes, so mine is:

```
getmail_fetch --delete --timeout=30 **myISPmailserver** **myISPlogin** **myISPpassword** '| /usr/bin/zarafa-dagent -s **myZarafaUserName**'
```

---

### Post by w00ter on 2008-11-21
Hi Matt,

Finaly got around to reinstalling Ubuntu and Zarafa, just got one question. With "you dont have to make any changes to master.cf", do you mean the default postfix master.cf or the one posted by E-jey in the first guide? 

Thanks :)

---

### Post by mattbourne on 2008-11-21
twizzle - thanks for that.  i'll try it this weekend :).

w00ter - my master.cf is exactly as it came out of the box after i chose the "Internet Site" option after typing "apt-get install postfix" (click OK and then chose Internet Site and you just then need to amend the main.cf as described above)

matt

---

### Post by w00ter on 2008-11-21
> **mattbourne said:**
> twizzle - thanks for that.  i'll try it this weekend :).

w00ter - my master.cf is exactly as it came out of the box after i chose the "Internet Site" option after typing "apt-get install postfix" (click OK and then chose Internet Site and you just then need to amend the main.cf as described above)

matt
Thanks Matt! 

It looks like I got it running.. and without any error message in the log files! woohoo! Only problem I have now is with the SMTP receiving part, but it's starting to look good! 

btw. could you post your main.cf and master.cf files? As I chose 'no configuration' during the postfix install. 

Thanks :D

---

### Post by mattbourne on 2008-11-21
master.cf
------------------
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

---

### Post by mattbourne on 2008-11-21
main.cf ****where i have inserted ubuntu.com you need to change this for your own server name****
----------------

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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = ubuntu.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ubuntu.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

mailbox_command = /usr/bin/zarafa-dagent "$USER"

---

### Post by Twizzle on 2008-11-22
Matt

I have worked it out.

I was having no luck with getmail so tried fetchmail and using a couple of theads ([here]("http://www.howtoforge.com/debian_etch_fetchmail") and [here]("http://forums.zarafa.com/viewtopic.php?f=9&t=1036&p=4194&hilit=MDA+returned+nonzero+status+70#p4194")) I managed to get it to work.

My /etc/fetchmailrc file is:

```
# /etc/fetchmailrc for system-wide daemon mode
# This file must be chmod 0600, owner fetchmail

set daemon        300                # Pool every 5 minutes
set syslog                        # log through syslog facility
set postmaster  root

set no bouncemail                # avoid loss on 4xx errors
                                # on the other hand, 5xx errors get
                                # more dangerous...

##########################################################################
# Hosts to pool
##########################################################################

# Defaults ===============================================================
# Set antispam to -1, since it is far safer to use that together with
# no bouncemail
defaults:
timeout 300
antispam -1
batchlimit 100

poll ***myISPserver***
with protocol POP3
user ***"me@myISP.co.uk"***
password ***"secret"***

fetchall
mda "/usr/bin/zarafa-dagent ***john***"

```

I then added 'fetchmail' to my local_admin_users option in /etc/zarafa/server.cfg, ran:

```

chmod 600 /etc/fetchmailrc
chown fetchmail /etc/fetchmailrc

```

Edited /etc/default/fetchmail to make it run as a daemon,

rebooted (old windows habits die hard!)

and it worked!

---

### Post by Twizzle on 2008-11-22
I am now trying to send mail using postfix and am getting the following error when I try and start postfix:

```
postfix: fatal: /etc/mailname: cannot open file: No such file or directory
```

If I create that directory I get an error about having two hard links... I really am lost at this stage!

---

### Post by mattbourne on 2008-11-22
Twizzle,

I had that problem in one of my previous attempts.  I think it came from when i installed postfix by chosing the "No Configuration" option.  This is the link i found to correct it...
[http://lists.debian.org/debian-user/2003/10/msg05051.html](http://lists.debian.org/debian-user/2003/10/msg05051.html)

matt

---

### Post by mattbourne on 2008-11-22
thanks for the info on fetchmail.  ive got it working now too.  i couldnt use the last line of your config file, i had to revert to the one in the guide on howtoforge but all is great :)

Ive nearly finished my guide on how i have set this up so i'll post it once ive added this bit in (but my mouse has run out of power and is about to go back on charge!!!).

Thanks for all your help guys :)

matt

---

### Post by w00ter on 2008-11-26
Just an update from my side.. 

I'm still having trouble getting the 'receiving e-mail' part to work. I think it's a SMTP issue, since I have to change my SMTP port to something other than 25, which I have (+ account at rollernet.us)4. 

Anyway.. just to let you guys know I havent given up... yet ;)

---

### Post by mattbourne on 2008-11-26
my guide is almost ready.  i just want to convert it to pdf and then ill put a link to it on here.  maybe that would be of some use to you???

matt

---

### Post by w00ter on 2008-11-26
Yeah that would be fantastic Matt! It'd be great to have a 'working' guide so I can figure out what I'm doing wrong! 

Looking forward to it ! Big thanks for taking the time to do this!

---

### Post by Twizzle on 2008-11-26
That would help me too. I am still having problems sending mail through my ISP server (1and1).

I have changed the line in my spooler.cfg to:
```
smtp_server     =       auth.smtp.1and1.co.uk
```

but my spooler.log gives me:

```
Wed 26 Nov 2008 19:26:34 GMT: SMTP: Error while executing command 'DATA'. Response: 550 must be authenticated
Wed 26 Nov 2008 19:26:34 GMT: 0xb74b2b90: E-mail for user john could not be sent, notifying user
Wed 26 Nov 2008 19:26:34 GMT: 0xb74b2b90: Removing failed message from queue

```

I have followed [**this**]("http://freelock.com/kb/Postfix_relayhost") guide to try and set up authentication but I don't know where I am going wrong!

---

### Post by mattbourne on 2008-11-27
Im too having some trouble sending email.  Zarafa wont allow you to use a different SMTP server, i have already researched this.  you'll need to have a static IP address to be able to send email.  Last night i could send them from within the webaccess but not from my mac, or iPhone.  At the moment i get this error message in my spooler.log:

E-mail for user XXXXXX could not be sent, notifying user

---

### Post by mattbourne on 2008-11-27
just been doing a little searching and found someone who needs to restart the spooler before it will work.  I needed to reboot my PC yesterday evening and my zarafa is running as a VM on my PC.  This is now working on my iPhone and the webaccess.

Now im trying to figure out how to send emails via my mac as it asks for a server and keeps rejecting whatever i try :S

---

### Post by mattbourne on 2008-11-27
guys,

sorry its taken so long, adobe wasnt working properly on my PC so i couldnt convert it to PDF at home so I had to take it to work to do.

In any case, here are my instructions: [http://www.mattbourne.com/ubuntuinstruction.pdf](http://www.mattbourne.com/ubuntuinstruction.pdf) - let me know how you get on with them and if I have any errors.  If the link doesnt work, try again later as my server or net connection might be down (the link is definitely correct!!).

matt

---

### Post by w00ter on 2008-11-28
Awesome Matt, the guide is looking good! I'm going to go through it today if it's not too busy at work ;) 
So far I've only messed around with webaccess and trying to get that to work, next step is to try push. 

About sending e-mails.. I've set the smtp address of my own webhost (which doesnt require authentication) in spooler.cfg, and it works. 

I read that it should work with SASL.. but I see you guys been busy with that already..

ps. I upgraded to Zarafa Beta 5.. and webaccess is waaay faster :)

---

### Post by mattbourne on 2008-11-28
how did you get the smtp server to work??  I spent some time looking for that last night.

From doing some reading, you shouldnt need to change the smtp server with zarafa if it works from within the webaccess.  i can now send via my iphone and webaccess but not from my PC or mac.  I think this is to do with how i have set them up individually (i cant even access my inbox from Outlook at the moment although it acknowledges unread messages in there).

I just hope the next release of zpush includes html emails because getting them in plain text is very annoying :(

---

### Post by w00ter on 2008-11-28
Yay! I figured out why I couldnt receive e-mail.. all e-mails sent to my domain were denied by rollernet.us. It's still not 100% operational yet though.. (DNS updates still required one some servers). 

I havent been able to SEND e-mail using my own server, so I used my webhost's one, without authentication. If I get it running through my own, I'll let you know right away! 

btw. your guide is excellent and detailed! Thanks!

---

### Post by ferrerpheonix on 2008-12-01
Hi there,

Thanks MattBourne and everyone else for this great collection of info.
I'm getting similar, but unfixable problems.
Followed all advice in this thread, I'm running Ubunu Hardy and it seems basically postfix won't run. I did the initial install following the first howto, and installed postfix with no config. It now has all of MattBournes changes in it.
If I type sudo postfix start, then sudo pico /var/log/mail.log is see this:

Dec  1 23:27:09 Barney postfix/master[4133]: fatal: /etc/postfix/master.cf: line 67: bad transport type: user=vmail

Any ideas?

I'm fairly new to Linux but good at following instructions :)

---

### Post by Twizzle on 2008-12-02
I ended up installing postfix with the Internet option, as Matt suggested.

Try removing postfix - apt-get remove --purge postfix

and re installing but select Internet

Also, the guides / suggestions on here are a bit different - did you try Matts pdf instruction sheet?

---

### Post by ferrerpheonix on 2008-12-02
Yup, your totally right, I ended up just doing that, and its all good. I wonder if its worth updating the very valuable howto...

thanks again. I'm going onward to battle with tomcat now... :(

---

### Post by Twizzle on 2008-12-02
Oh and Matt, let me know if you are still having problems with sending mail from your phone etc. I think I have it all up and running, I can sent from webaccess at home, from my mobile and now I just need to try webaccess from work.

I won't post my main.cf yet as I think it still has some bits in it I don't need and don't want to confuse the issue.

---

### Post by mattbourne on 2008-12-02
Hi Twizzle,

I can send email no problem from my iPhone, PC and webaccess now; its just my Mac im having trouble with - it keeps asking me for an SMTP server but i think this could be a local problem as Zarafa needs to be the default mail account and I also have another set up on there.

The only other problem im having is remembering to restart the zarafa-spooler after rebooting my server.  Lets hope that bug is fixed in the next release :).

matt

---

### Post by Twizzle on 2008-12-02
I may have spoken too soon! 

I am having problems sending email from Thuderbird on my main PC through my server and onto my ISP (which works with web access and my phone). Looking at my mail.log it appears to be a problem with authorising me for some reason. It is the same passeword as I use to log into the server and read my mail which works.

I am at work at the moment so can't post the error log - will do later.

---

### Post by ferrerpheonix on 2008-12-02
Guys,

Sorry if this is a bit offtopic.
I got everything working, but sending mail. I'm Ubuntu Hardy, Zarafa, Postfix.
Webmail works, i can send mail.
IMAP works over ssl, I can login in mail.app on my osx workstation and pull down my mail

But how do I setup SMTP so I can send mail from mail.app? Do i need to also create a postfix user, or is this meant to be handled by Zarafa?

Bit confused.

---

### Post by ferrerpheonix on 2008-12-02
After some research, it appears its not possible to setup SMTP AUTH using postfix and the zarafa usernames... oh well. Not quite sure what to do.

One more (last one I promise) question.
Matt I have an iPhone 3g, I have setup z-push in this article, I can login to the URL and I get the expected "PUT not supported, you must have an active sync device" message.

But if I setup my iPhone, create a new mail account and select exchange, enter in the IP address of my Zarafa box, the iPhone just says after a minute, "cannot verify exchange account". I can't get it too connect to z-push, did yours just work first time?

I'm not quite sure what to debug, the URL on the server works fine...

---

### Post by mattbourne on 2008-12-02
Hi,

I too am having trouble getting mail sent via mail.app in OSX.  I havent figured out a way to get mail to send via Zarafa rather than OSX.

With zpush, what happens when you go to [www.yourserver.com/Microsoft-Server-ActiveSync](www.yourserver.com/Microsoft-Server-ActiveSync) ???  Can you log in using your administrator Zarafa credentials??  Have you followed my guide in a previous post??

When it says "cannot verify account, click on "finish" or "next" or whatever is in the top right hand corner and it will accept the settings - the reason it fails is because its not encrypted data.

matt

---

### Post by ferrerpheonix on 2008-12-02
I added a post to Zafara forums but no luck.
Seems like a major oversite, only idea I have is setup SMTP AUTH seperatly on postfix, and share the user/pass to my users.

on the iphone, I tried just clicking continue after it tells me that it cannot verify my details. Then it still fails to connect. I'm just entering my Zafara servers IP address as the exchange server, is that correct?

If I go to my zafara server/Microsoft_Ac.. i get a logon, i can logon, and I get the message I need to use a supported device, so it all looks fine there...

---

### Post by mattbourne on 2008-12-02
do you have wifi turned on or 3g??  are you entering your internal IP address or your external address and do you have port 236 forwarded from your router to your server??

---

### Post by ferrerpheonix on 2008-12-02
My Zarafa box is in a datacenter (slicehost). It has an external IP. I'm setting up my iphone at home, with that external IP. 
Its just pretty hard to debug because the server says its happy, and iphone say, well, nothing other than "no" :)

---

### Post by mattbourne on 2008-12-02
mmm... im afraid i dont think i'll be able to help here as i havent had the problems you are experiencing.  my exposure to zarafa and postfix is very limited and the majority of my fault fixing has been described here.

have you tried asking on the z-push forum??

---

### Post by ferrerpheonix on 2008-12-02
Resolved, I had to ignore the errors the iphone gives setting it up, and then afterwards go into the iphone mail settings and advanced, and disable ssl.
Works a charm...

LAter I just enabled my site that has z-push installed to be accessible over SSL. Then no warning when setting up the iPhone.

Now to try and setup this bloody relay issue!

---

### Post by ferrerpheonix on 2008-12-03
Hey Matt,

I was posting in Zarafa forums, and this might work... 

[http://forums.zarafa.com/viewtopic.php?f=9&t=1424&p=5982#p5982](http://forums.zarafa.com/viewtopic.php?f=9&t=1424&p=5982#p5982)

---

### Post by ferrerpheonix on 2008-12-04
I have been struggling trying to get saslauthd enabled so my clients can authenticate on SMTP to send mail through the server as well as receive it. The instructions on the forum i posted above, seem to be good. Trouble is I don't have saslauthd installed, and I don't want to mess up my postfix config that finally started working!

So I'm in the process of setting up a VM to try and test it, is anyone else interested in this setup?

---

### Post by w00ter on 2008-12-04
I think it will be of great value if you are able to figure out how to get this working. Afterall, most SMTP servers require authentication :)

Good luck and keep us updated Ferrer! :D

---

### Post by ferrerpheonix on 2008-12-04
CAn anyone see an issue to running this apt-get after everything in this tuturial, any conflicts? 

apt-get install libsasl2 sasl2-bin libsasl2-modules libdb3-util procmail

---

### Post by Wildfire@home on 2009-02-09
The problem with this file is that some lines are not displayed correctly. If you see (in your browser) a line followed by another line starting with "flags" the second line has to start with a whitespace. The browser is suppressing this, but of you qouted one of the master.cf files here you would see it.

So for all those who tried postfix, go to the lines in question and escape the NEXT line by adding a whitespace. So a line staring with flags should start with <blank>flags in your file.

---

### Post by doudoufr on 2009-03-15
Hey People
I need your help.

So, first of all, sorry for my english, but i'm french...so...excuse me ! :D

So, i tried to set-up zarafa, and,...well it works...But i can't send any mails....always return to sender...i don't know why.

On every tutos i found on internet, it is not clear at all, how to set-up a mail server...pfiouuuu ! 

so...in france here, with my internet service provider, i can have a personal dns. for example, my internet box is reachable by is ip but also by a name like "totomachin.hd.free.fr"..

But nevermind, i don't care to send mail from totomachin.hd.free.fr or by my normal mail (example.free.fr).

So my question is : how do I setup postfix to send mail from zarafa (from totomachin.hd.free.fr or from example.free.fr) ??? what do I need to configure/change ?

i can connect to zarafa webaccess, and i have synced my windows mobile phone to. These things works.
The only things...i cant send anything. ! lol

please, be clear, detailed your answer, because i'm lost ! 

here is my main.cf and master.cf

main
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = blabla.hd.free.fr
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = blabla.hd.free.fr, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

mailbox_command = /usr/bin/zarafa-dagent "$USER"
```

master
```
#
# Postfix master process configuration file. For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ================================================== ========================
# service type private unpriv chroot wakeup maxproc command + args
# (yes) (yes) (yes) (never) (100)
# ================================================== ========================
smtp inet n - - - - smtpd
#submission inet n - - - - smtpd
# -o smtpd_tls_security_level=encrypt
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#smtps inet n - - - - smtpd
# -o smtpd_tls_wrappermode=yes
# -o smtpd_sasl_auth_enable=yes
# -o smtpd_client_restrictions=permit_sasl_authenticate d,reject
# -o milter_macro_daemon_name=ORIGINATING
#628 inet n - - - - qmqpd
pickup fifo n - - 60 1 pickup
cleanup unix n - - - 0 cleanup
qmgr fifo n - n 300 1 qmgr
#qmgr fifo n - - 300 1 oqmgr
tlsmgr unix - - - 1000? 1 tlsmgr
rewrite unix - - - - - trivial-rewrite
bounce unix - - - - 0 bounce
defer unix - - - - 0 bounce
trace unix - - - - 0 bounce
verify unix - - - - 1 verify
flush unix n - - 1000? 0 flush
proxymap unix - - n - - proxymap
proxywrite unix - - n - 1 proxymap
smtp unix - - - - - smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay unix - - - - - smtp
-o smtp_fallback_relay=
# -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq unix n - - - - showq
error unix - - - - - error
retry unix - - - - - error
discard unix - - - - - discard
local unix - n n - - local
virtual unix - n n - - virtual
lmtp unix - - - - - lmtp
anvil unix - - - - 1 anvil
scache unix - - - - 1 scache
#
# ================================================== ==================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe( delivery
# agent. See the pipe( man page for information about ${recipient}
# and other message envelope options.
# ================================================== ==================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop unix - n n - - pipe
flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp unix - n n - - pipe
flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail unix - n n - - pipe
flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp unix - n n - - pipe
flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix - n n - 2 pipe
flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman unix - n n - - pipe
flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
${nexthop} ${user}
```

my spooler.cfg
if i enter "smtp.free.fr" (isp smtp) on "smtp_server" it also doesn't work. (and i don't understand, because to connect to my isp smtp, i need a username, and password, but ....in this file, there is no username, password.....)
```
##############################################################

# SPOOLER SETTINGS



# Outgoing mailserver name or IP address

smtp_server	=	localhost



# Server unix socket location

server_socket	=	file:///var/run/zarafa



# drop privileges and run the process as this user

run_as_user = 



# drop privileges and run the process as this group

run_as_group = 



# create a pid file for stopping the service via the init.d scripts

pid_file = /var/run/zarafa-spooler.pid



# run server in this path (when not using the -F switch)

running_path = /



##############################################################

# SPOOLER LOG SETTINGS



# Logging method (syslog, file)

log_method	=	file



# Loglevel (0=no logging, 5=full logging)

log_level	=	3



# Logfile for log_method = file

log_file	=	/var/log/zarafa/spooler.log



# Log timestamp - prefix each log line with timestamp in 'file' logging mode

log_timestamp	=	1





##############################################################

# SPOOLER SSL LOGIN SETTINGS

# 

# Note: server_socket must be set to https://servername:portname/zarafa

#       to use this type of login method



# Login to the Zarafa server using this SSL Key

sslkey_file = /etc/zarafa/ssl/spooler.pem



# The password of the SSL Key

sslkey_pass = replace-with-server-cert-password



##############################################################

# SPOOLER THREAD SETTINGS



# Maximum number of threads used to send outgoing messages

# Default: 5

max_threads = 5



##############################################################

# SPOOLER FAXING SETTINGS



# When sending an email that must go to a fax address, the address

# will be rewritten to <phonenumber>@<fax_domain>

fax_domain = fax.local



# If the received number starts with a '+', it will be replaced by

# the fax_international value.

# eg. +3112345678@fax.local will be rewritten to 003112345678@fax.local

fax_international = 00



##############################################################

# SPOOLER DELEGATE SETTINGS



# Set this value to 'yes' to let the spooler always send emails with

# delegates (other user than yourself in the From: header)

# In installations before 6.20, this value was always 'yes'

always_send_delegates = no

```

So, what i have done wrong ? what do I need to configure ? i'm stuck !

thanks for the help ppl !


_**[COLOR="Red"][Edit 16 march 2009][/COLOR] : I don't know why, I don't know how, but it works ! I just reinstalled postfix, and now i can send email...! hihi ! so happy I am ! **_

---

### Post by sixit on 2009-04-28
> **mattbourne said:**
> 
I just hope the next release of zpush includes html emails because getting them in plain text is very annoying :(

If you think that is annoying, try preferring plain text and getting html!

---

### Post by mannibr on 2009-05-04
> **mattbourne said:**
> I just hope the next release of zpush includes html emails because getting them in plain text is very annoying :(

Hi,

yes, the next z-push version will have html email support and some more nice features like search in global address book, pictures of contacts.


Greets.

---

### Post by RonFinegan on 2009-07-20
Hi All I am new to zarafa and this forum. Can I just say thanks to Matt for a great install guide, simple step by step instruction "Great"? Thought these few things I came across along the way may help/add to the instructions. Your own ISP uses reverse lookup to verify the email comes from one of there IP addresses if so it allows with out authentication.

So to send mail using your ISP
In  "/etc/postfix/main.cf" Add your ISP SMTP Server
relayhost =  my.isp&#8217;s.smtp.server
(this is how I got round the Authentication issue)

To increase maximum attachment size
In "/etc/php5/apache2/php.ini"
change
post_max_size = 30M
and in "/var/www/webaccess/.htaccess"
change
php_value post_max_size 30M
php_value upload_max_filesize 30M

To send using different email addresses i.e. Google & hotmail as well as your domain addresses
In  "/etc/zarafa/spooler.cfg"
Change
always_send_delegates = yes

#####postfix relay smtp authentication##########

*atp-get install libsasl2-modules *

also ensure that the following are installed *postfix-tls libsasl-modules-plain sasl-bin*

Then follow the link below for directions
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html]("http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailservers.html")

hope this helps anyone else trying to tweak there server.
###########postfix message size limit######
add the following to postfix main
 message_size_limit = 104857600
this will prevent postfix from stopping large emails

---

### Post by palcica on 2009-08-02
Ok, everything is workin fine... But now I have another question. How to install spam filter and antivirus for zarafa?!?
Please, need help :(

---

### Post by RonFinegan on 2009-09-22
check out this thread in the Zarafa forum:

[http://forums.zarafa.com/viewtopic.php?t=74&f=11](http://forums.zarafa.com/viewtopic.php?t=74&f=11)

i use clamav.net for antivirus

SpamAssassin is good for spam but i find the best thing to do is use a service (this reduces your work load updating it) something like email laundry.
theemaillaundry.com

Have fun

---

### Post by hydra666 on 2009-09-23
Hi,

I have installed [ASSP]("http://assp.sourceforge.net/") with clamav.
ASSP is, imo, the best free antispam system available. 
Spam has reduced dramatically.
Its very easy to set up with zarafa/postfix.

---

### Post by HDave on 2009-11-12
Anyone here have a good way to sync contacts between Thunderbird and Zarafa?

---

### Post by artic112 on 2009-11-13
> **HDave said:**
> Anyone here have a good way to sync contacts between Thunderbird and Zarafa?

HDave, 
I have asked the Zarafa support for this and they did not have anything for this.
There is a Zimbra plugin where the developer says that he will develop it if enough people show interest for it.

---

### Post by HDave on 2009-11-13
I added my name to 40+ other people on the Zindus site and also emailed the develop who said their are no near term plans.

I look that the source code for the add-in, and frankly it doesn't seem like it would be that hard to make it work with Zarafa, but he doesn't have the time....and neither do I right now.

---

### Post by doudoufr on 2009-11-27
> **hydra666 said:**
> Hi,

I have installed [ASSP]("http://assp.sourceforge.net/") with clamav.
ASSP is, imo, the best free antispam system available. 
Spam has reduced dramatically.
Its very easy to set up with zarafa/postfix.

and how do you do this ? lol !
on the wiki on assp, they talk about exim, not postfix.
At a moment, they said to change smtp to port 26. Do we need to do that in postfix ?
well, for me, not so easy to set up with zarafa and postfix. 

A good explanation will be so sooo much greaaat ! :p:p

---

### Post by Yfrwlf on 2010-04-18
Can't wait to see this get packaged for Lucid Lynx.  Hopefully its installation and setup will be easier. ^^

Would be great to see it in the repos, too.

---

### Post by ashish@# on 2011-02-10
how to replace mysql database file in ubuntu
pls........... send solution

---

### Post by lemonidas on 2011-03-31
Silly question

Can I use Zarafa+zpush to store+sync contacts and calendars but not for email?

Meaning I don't want to setup email at all. I already have a working mail server that I would prefer not to mess with (plus it's on a freeBSD box that I think zarafa would be hell to install)
:confused:

---

