---
title: "Howto: set up a mail server in Ubuntu"
date: 2005-12-01
forum: Outdated Tutorials &amp; Tips
---

### Post by flurdy on 2005-12-01
The [how to set up a mail server on a GNU / Linux system]("http://flurdy.com/docs/postfix/") guide has been upgraded to breezy from hoary.

It is a complete step by step guide to install, configure and run these packages:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail+Postgrey

Please discuss in this thread any issues or comments regarding this, the 4th edition.

Specifically the SASL section might need testing, as some of the packages has changed since hoary.

Edition 3, the hoary version, is discussed in [this thread ]("http://ubuntuforums.org/showthread.php?t=40047"). Some issues might have already been discussed in that thread.

---

### Post by dcostelloe on 2005-12-02
:p 

Thanks I have my mail server running with breezy.

php4-pear 
php4-cli

Missing from document as required installs. I did go back to 3rd addition to locate them.

Thanks

---

### Post by flurdy on 2005-12-13
Updated the SASL packages so it works perfectly in breezy

---

### Post by ember on 2005-12-13
Great - as I am about to set up exactly this thing, I guess, it will save many hours of doc-reading and google.
Thanx.

---

### Post by Zandaa on 2005-12-13
flurdy, this all seems pretty cool and all, but I can't set up the shorewall, there's only a shorewall.conf inside the directory, I dunno if I missed something (can't start up the firewall because it says no zones are defined)

---

### Post by flurdy on 2005-12-13
see the os section of the configure bit

---

### Post by LtDan on 2005-12-13
Great Howto!!!

I have set this up on my server, however I had hit a small snag.  Postfix as of 2.2 I believe, has TLS support built in.  However according to Postfix's website, it is turned off by default.  Therefore there is no Postfix-tls package in any of the breezy badger repositories.  (This sent me for a loop untill I found out it's built in now)

---

### Post by flurdy on 2005-12-13
yes, when doing the apt-get with breezy, it will just say there is no need for postfix-tls as long as in the same apt-get you install postfix.

---

### Post by Zandaa on 2005-12-13
[quote="howto page"] First set your server name, this must match what you put in your domains DNS MX records.[/quote]
what are my DNS MX records??? I've never heard anything about those :confused: :confused: :confused:

---

### Post by obscenic on 2005-12-17
I've set up with this how-to, and have been stopped in the testing.  I restart, or start postfix with the init.d and it doesn't show up in netstat... telnet on 25 connects, but doesn't give responses.

How can I make postfix start properly?

---

### Post by flurdy on 2005-12-21
[QUOTE=obscenic]I've set up with this how-to, and have been stopped in the testing.  I restart, or start postfix with the init.d and it doesn't show up in netstat... telnet on 25 connects, but doesn't give responses.

How can I make postfix start properly?[/QUOTE]

The /var/log/mail.log should tell you what is wrong.

---

### Post by lreyes6 on 2005-12-21
hi... i'm starting to read the guide seems to be very usefull,  just a little thing, there's a broken link in this section 
> 
Packages

Here is a list of packages needed, and what they provide. Some are required by several of the software, some might not be needed if you are not fully following this howto. Please note the [extended section]("http://flurdy.com/docs/postfix/extend") require further packages. 

the link for the extended section is broken

---

### Post by rabid on 2005-12-21
Flurdy, thanks for the great HOWTO.

I started with a fresh Ubuntu install and worked my way through your setup from top to bottom but I've run into a small snag. While testing in a telnet session I get an access denied error in mysql.info immediately after closing the data field of the email. [email]Postfix@localhost.loca[/email]ldomain is trying to connect instead of the mail user I setup in sql and in all of the postfix_*.conf files. This test is with all content filtering turned off. If I turn the filtering on, I get a different error (Can't connect to 127.0.0.1 port 10025, Connection refused at /usr/sbin/amavisd-new line 2912, <GEN9> line 34.) but in exactly the same spot.

What have I buggered up?

---

### Post by evs on 2005-12-21
[QUOTE=lreyes6]the link for the extended section is broken[/QUOTE]

It's a section farther down on the page-
[http://flurdy.com/docs/postfix/#extend](http://flurdy.com/docs/postfix/#extend)

---

### Post by flurdy on 2005-12-21
[QUOTE=rabid]Flurdy, thanks for the great HOWTO.

I started with a fresh Ubuntu install and worked my way through your setup from top to bottom but I've run into a small snag. While testing in a telnet session I get an access denied error in mysql.info immediately after closing the data field of the email. [email]Postfix@localhost.loca[/email]ldomain is trying to connect instead of the mail user I setup in sql and in all of the postfix_*.conf files. This test is with all content filtering turned off. If I turn the filtering on, I get a different error (Can't connect to 127.0.0.1 port 10025, Connection refused at /usr/sbin/amavisd-new line 2912, <GEN9> line 34.) but in exactly the same spot.

What have I buggered up?[/QUOTE]

by postfix_*.conf i presume you are using a different naming convention than from the howto. are there other lines in your set up that could be using mysql? 

could you post the relevant lines in main.conf and the mysql cf files (without the pw offcourse)?  

as for the amavis errors, have you specified it correctly in the master.cf?

---

### Post by rabid on 2005-12-21
My bad...had postfix on the brain. postfix_*.conf = mysql_*.cf.  I did however get the original problem worked out. I had a spelling error in mysql_mailbox.cf. user**r**=mail. I'm gussing this caused it to default to postfix@localhost for a user. Still getting the Amavis error, but I'll keep troubleshooting that and post again if I can't get anywhere.

Thanks for making me look at my .cf files one last time. I didn't notice the error until I was pasting it into this message.

-rabid

---

### Post by craty on 2005-12-21
hi,
i am quite excited reading this aritcle that i can have my own mail server. i am connected to internet through** proxy servers** and also behind **some firewalls** as ours is an **university lan.** so i would like to know **what all ports are required to opened to setup a mail server (also let me know if there are any other requirements **) which can be accessed by outside world.

So please let me know list of ports required to opened, so that i can enquire about that. 

thanx

---

### Post by rsgooch on 2005-12-21
[QUOTE=craty]hi,
i am quite excited reading this aritcle that i can have my own mail server. i am connected to internet through** proxy servers** and also behind **some firewalls** as ours is an **university lan.** so i would like to know **what all ports are required to opened to setup a mail server (also let me know if there are any other requirements **) which can be accessed by outside world.

So please let me know list of ports required to opened, so that i can enquire about that. 

thanx[/QUOTE]

The only port requred for email is port 25.  You will have to setup a mx record on the dns serving you domain on the internet to forward mail to your domain.  You will probably have to setup NAT to forward all trafiic on port 25 to your server and bob's your uncle.

Later

---

### Post by rabid on 2005-12-21
Welp, Amavis is outsmarting me. I've gone over it a few times now and I can't find any errors anywhere in the amavis.conf or postfix's master.cf. Here's the full error message from the mail.info log:

**Dec 21 16:03:56 localhost postfix/smtp[18126]: CA862424B: to=<user1@localhost.ca>, relay=127.0.0.1[127.0.0.1], delay=3667, status=deferred (host 127.0.0.1[127.0.0.1] said: 450 4.4.1 Can't connect to 127.0.0.1 port 10025, Connection refused at /usr/sbin/amavisd-new line 2912, <GEN9> line 34., id=17864-02 (in reply to end of DATA command))**

***note:** the <user1@localhost.ca> is a stand-in for the actual username and domain name which is being read correctly.

And here are the entries in */etc/postfix/master.cf* regarding amavis:

[B]smtp      inet  n       -       -       -       -       smtpd
        -o cleanup_service_name=pre-cleanup

cleanup   unix  n       -       -       -       0       cleanup
        -o mime_header_checks=
        -o nested_header_checks=
        -o body_checks=
        -o header_checks=

amavis    unix  -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes

127.0.0.1:120025 inet   n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_client_restrictions=
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o strict_rfc821_envelopes=yes
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1001

pre-cleanup unix        n       -       -       -       0       cleanup
        -o virtual_alias_maps=
        -o canonical_maps=
        -o sender_canonical_maps=
        -o recipient_canonical_maps=
        -o masquerade_domains=[/B]

I went over my amavis.conf again and see no differences between what the howto says and what I have and I've rechecked the permissions on /var/lib/amavis/tmp and virusmails.

Any ideas?

---

### Post by amcavoy on 2005-12-21
I have followed the steps, but I get the following error when I attempt to login:

> ERROR: Bad request: The IMAP server is reporting that plain text logins are disabled. Using CRAM-MD5 or DIGEST-MD5 authentication instead may work. Also, the use of TLS may allow SquirrelMail to login. Please contact your system administrator and report this error.

Any ideas?

---

### Post by strag on 2005-12-22
Alright, I've followed this howto through however in the mail.log I keep getting the following error popping up whenever I try to send anything, and obviously the mail never sees the light of day again...

```
Dec 22 09:25:37 localhost master[13348]: fatal: master_spawn: exec /usr/lib/postfix/2: No such file or directory
Dec 22 09:25:38 localhost postfix/master[13324]: warning: process /usr/lib/postfix/2 pid 13348 exit status 1
Dec 22 09:25:38 localhost postfix/master[13324]: warning: /usr/lib/postfix/2: bad command startup -- throttling
```

For the life of me I can't figure out why it's trying to run /usr/lib/postfix/2, there's a number of other executables in there but no 2, and search as I may I can't even find references to anything like this. Any help you could offer would be greatly appreciated.

---

### Post by flurdy on 2005-12-22
[QUOTE=strag]Alright, I've followed this howto through however in the mail.log I keep getting the following error popping up whenever I try to send anything, and obviously the mail never sees the light of day again...

```
Dec 22 09:25:37 localhost master[13348]: fatal: master_spawn: exec /usr/lib/postfix/2: No such file or directory
Dec 22 09:25:38 localhost postfix/master[13324]: warning: process /usr/lib/postfix/2 pid 13348 exit status 1
Dec 22 09:25:38 localhost postfix/master[13324]: warning: /usr/lib/postfix/2: bad command startup -- throttling
```

For the life of me I can't figure out why it's trying to run /usr/lib/postfix/2, there's a number of other executables in there but no 2, and search as I may I can't even find references to anything like this. Any help you could offer would be greatly appreciated.[/QUOTE]

I bet a line your master.cf startes with 2 ?

Remember if a property spans many lines the additional lines must be prefixed with tabs or spaces.

---

### Post by flurdy on 2005-12-22
[QUOTE=rabid]Thanks for making me look at my .cf files one last time. I didn't notice the error until I was pasting it into this message.
-rabid[/QUOTE]
Thats the way it works. 
Often I bang my head against the screen for hours, but as soon as I ask a collegue for input, the process of describing the problem often makes it obvious to myself what is wrong.

---

### Post by flurdy on 2005-12-22
[QUOTE=amcavoy]I have followed the steps, but I get the following error when I attempt to login:
Any ideas?[/QUOTE]

Looks like you are using squirrelmail, does normal imap work okay?
Seems Squirrelmail has been set to use SASL authentication, but courier has not been set to use SASL

---

### Post by flurdy on 2005-12-22
[QUOTE=rabid] Can't connect to 127.0.0.1 port 10025

127.0.0.1:120025 inet   n       -       -       -       -       smtpd[/QUOTE]

Amavis has been set to use port 10025, while postfix has been set to connect to amavis on port 120025?

---

### Post by rabid on 2005-12-22
[QUOTE=flurdy]Amavis has been set to use port 10025, while postfix has been set to connect to amavis on port 120025?[/QUOTE]

taynk u fore hellpin me wiff my redin dis-able-ity.

:p 

Thanks again, Ivar.

-rabid

---

### Post by strag on 2005-12-22
[QUOTE=flurdy]I bet a line your master.cf startes with 2 ?

Remember if a property spans many lines the additional lines must be prefixed with tabs or spaces.[/QUOTE]

Not quite the problem, but it put me on the right track... had one too many -'s on one of my lines... Makes ya feel like an idiot when you do that... :???:

---

### Post by amcavoy on 2005-12-22
[QUOTE=flurdy]Looks like you are using squirrelmail, does normal imap work okay?
Seems Squirrelmail has been set to use SASL authentication, but courier has not been set to use SASL[/QUOTE]
I am using uw-imapd.  I can't fix my problem for anything!  Thanks for the help :smile:

---

### Post by lreyes6 on 2005-12-22
hi... i'm kind a newb in this... i'm following the guide as is but i get in this part in red text
> 
Edit imapd (located in /etc/courier/)
# set how many connections to use per person. Easy to underestimate if you have 6 mailboxes set up. 
MAXPERIP=20 
# high debug to start with 
DEBUG_LOGIN=2 
IMAPDSTART=YES
[quote]
**[COLOR=Red]Then edit the same in the pop and ssl options, if you are going to use them. [/COLOR]**
 [/quote] 
where are the files? i mean i just need the pop file but i don't know where to find it... if edit this /etc/courier/pop the file is blank... i'm lost.


thanks

---

### Post by flurdy on 2005-12-22
[QUOTE=lreyes6]hi... i'm kind a newb in this... i'm following the guide as is but i get in this part in red text
 
where are the files? i mean i just need the pop file but i don't know where to find it... if edit this /etc/courier/pop the file is blank... i'm lost.


thanks[/QUOTE]

Sorry, my howto only install the IMAP packages, as there is no need for POP when IMAP is available. However if some prefer pop or need to fetch mail then install the courier-pop and courier-pop-ssl packages, which will in turn create the files needed

---

### Post by manemannen on 2005-12-23
Thanks for an excellent guide!

Unfortunately I encountered a problem. I get the following error in the postfix log:

"warning: connect to mysql server 127.0.0.1: Client does not support authentication protocol requested by server; consider upgrading MySQL client"

According to mysql.com I need to upgrade the client libs. Which ones should I upgrade?

And if I run:
dpkg --list | grep mysql

ii  courier-authmysql                     0.47-3ubuntu7.1              Courier Mail Server - MySQL authentication
ii  libdbd-mysql-perl                     2.9007-1                     A Perl5 database interface to the MySQL data
ii  libmysqlclient10                      3.23.56-3                    LGPL-licensed client library for MySQL datab
ii  libmysqlclient14                      4.1.12-1ubuntu3.1            mysql database client library
ii  mysql-client-4.1                      4.1.12-1ubuntu3.1            mysql database client binaries
rc  mysql-common                          4.0.24-10ubuntu2             mysql database common files (e.g. /etc/mysql
ii  mysql-common-4.1                      4.1.12-1ubuntu3.1            mysql database common files (e.g. /etc/mysql
rc  mysql-server-4.1                      4.1.12-1ubuntu3.1            mysql database server binaries
ii  postfix-mysql                         2.2.4-1ubuntu2               MYSQL map support for Postfix


I dont use the ubuntu distribution of mysql-server-4.1 since this does not handle BLOBs very well. I have installed the original version of MySQL 4.1.16 and replaced the mysql* binaries in /usr/bin/. Could the pose a problem?

thanks

---

### Post by manemannen on 2005-12-23
Found a fix for it. jees - if I only had read the complete solutions at mysql.com the first time :/

---

### Post by dcostelloe on 2006-01-02
Hi,
Great job on the How To :KS 

I am getting this warning in the logs anything I should do?

Dec 30 08:38:40 localhost postfix/smtp[12852]: warning: problem talking to server private/tlsmgr: Connection refused

Thanks

---

### Post by rickyjones on 2006-01-09
I ran into an issue...

I've been following this guide as best as I could, not leaving out a single step. Now I'm in the testing stage. I try to login as "root@localhost," and I end up with the following error from SquirrelMail.

ERROR : Connection dropped by imap-server.

So I'm looking into it. I cat the contents of my /var/log/mail.log

Jan  9 18:46:47 aira imaplogin: authdaemon: starting client module
Jan  9 18:46:47 aira imaplogin: authdaemon: ACCEPT, username root@localhost
Jan  9 18:46:47 aira imaplogin: chdir /var/spool/mail/virtual//root/: No such file or directory
root@aira:/etc/postfix#


It looks like that "virtual//root" is where I'm having issues... any idea on how I can fix this?

Thanks!

-Richard

---

### Post by evs on 2006-01-09
[QUOTE=rickyjones]I ran into an issue...

I've been following this guide as best as I could, not leaving out a single step. Now I'm in the testing stage. I try to login as "root@localhost," and I end up with the following error from SquirrelMail.

ERROR : Connection dropped by imap-server.

So I'm looking into it. I cat the contents of my /var/log/mail.log

Jan  9 18:46:47 aira imaplogin: authdaemon: starting client module
Jan  9 18:46:47 aira imaplogin: authdaemon: ACCEPT, username root@localhost
Jan  9 18:46:47 aira imaplogin: chdir /var/spool/mail/virtual//root/: No such file or directory
root@aira:/etc/postfix#


It looks like that "virtual//root" is where I'm having issues... any idea on how I can fix this?

Thanks!

-Richard[/QUOTE]

The directory is not created until an email is sent to that address, and you can't login to SquirrelMail until the directory is created, so send yourself a test email from another account.  But it looks like you also have a problem with your MySQL setup, because you have too many /'s  in 'virtual//root'.  In the USERS table, check your HOME and MAILDIR fields, HOME should be '/var/spool/mail/virtual/', and MAILDIR should be 'root/' (with no '/' in front only at the end).  Try that.  I hope it helps.

---

### Post by lreyes6 on 2006-01-10
I was having the same problem of the double // and i fix it taking out the last / from the field 'home' in the users table... now i can login but this error come's out now
> ERROR : Could not complete request.
Query: CREATE "INBOX.Sent"
Reason Given: Cannot create this folder.
I think is a permission problem but where? any ideas? 
thanks

---

### Post by cdean on 2006-01-10
[QUOTE=rabid]
**Dec 21 16:03:56 localhost postfix/smtp[18126]: CA862424B: to=<user1@localhost.ca>, relay=127.0.0.1[127.0.0.1], delay=3667, status=deferred (host 127.0.0.1[127.0.0.1] said: 450 4.4.1 Can't connect to 127.0.0.1 port 10025, Connection refused at /usr/sbin/amavisd-new line 2912, <GEN9> line 34., id=17864-02 (in reply to end of DATA command))**
Any ideas?[/QUOTE]

I, too, am getting this same error.  I've gone over the configs probably three times now and can't figure it out.  I'm about 12 hours away from removing all the packages and configs and redoing it all from scratch.

---

### Post by wannabelinuxconvert on 2006-01-11
Is it possible to use this kind of setup with a dynamic ip address using something like dyndns.org !?

I read a similar article that did accomodate this, but it was using ArchLinux

[http://www.hypexr.org/linux_mail_server.php]("http://www.hypexr.org/linux_mail_server.php")

Thanks

Mic

---

### Post by vtec on 2006-01-12
A while back i set up a simple mail server, and did not use mySQL. Could someone tell me what is stored in the database they are setting up and why its a better to use then not??

---

### Post by vtec on 2006-01-12
Double Post, Sorry.

---

### Post by Stryker777 on 2006-01-18
Jan 18 10:51:07 ###-###-###-##-my-domain postfix/smtpd[14461]: NOQUEUE: reject: RCPT from commando.sender.com[###.###.##.##]: 554 <me@mydomain.com>: Relay access denied; from=<me@otherdomain.org> to=<me@mydomain.com> proto=ESMTP helo=<smtp.isp.com>

What can I do to resolve this?  Im sending from an offsite account.  I also tried the telnet and I get the same thing.  It puts it in que then it doesnt go anywhere.
Any help would be appreciated.

---

### Post by flurdy on 2006-01-19
[QUOTE=wannabelinuxconvert]Is it possible to use this kind of setup with a dynamic ip address using something like dyndns.org !?

I read a similar article that did accomodate this, but it was using ArchLinux

[http://www.hypexr.org/linux_mail_server.php]("http://www.hypexr.org/linux_mail_server.php")

Thanks

Mic[/QUOTE]

yes, thats no problem. Just make sure all your mx setting is directed to your dydns.org address.

ps. If you plan to backup other peoples mxs, ie act as a back up spool, then you need to manually or write a script to update the proxy_interface ip address every time you ip changes

---

### Post by flurdy on 2006-01-19
[QUOTE=vtec]A while back i set up a simple mail server, and did not use mySQL. Could someone tell me what is stored in the database they are setting up and why its a better to use then not??[/QUOTE]

Using local users is fine, however using a database is more flexible, as you can unlimited domains and users. and users can be the same or different on different domains.

The db stores domain, email addresses alias and users log in addresses.

---

### Post by flurdy on 2006-01-19
[QUOTE=lreyes6]I was having the same problem of the double // and i fix it taking out the last / from the field 'home' in the users table... now i can login but this error come's out now

I think is a permission problem but where? any ideas? 
thanks[/QUOTE]

Yes, the double slash is actually a bug, which can either be fixed by moding the line in couriers authmysql file or removing it from the db. I keep in it as it doesnt affect the system.

---

### Post by flurdy on 2006-01-19
[QUOTE=Stryker777]Jan 18 10:51:07 ###-###-###-##-my-domain postfix/smtpd[14461]: NOQUEUE: reject: RCPT from commando.sender.com[###.###.##.##]: 554 <me@mydomain.com>: Relay access denied; from=<me@otherdomain.org> to=<me@mydomain.com> proto=ESMTP helo=<smtp.isp.com>

What can I do to resolve this?  Im sending from an offsite account.  I also tried the telnet and I get the same thing.  It puts it in que then it doesnt go anywhere.
Any help would be appreciated.[/QUOTE]

Either:
commando.sender.com do not pass the helo restrictions
or [email]me@otherdomain.org[/email] do not pass the sender restrictions
or me@mydomain do not pass the recipient restricitions.
Or something else..

most likely is mydomain.com is not in your domain list, or [email]me@mydomain.com[/email] is not in you alias list.
Another issue is if the interface setting in main.cf is set properly?

---

### Post by flurdy on 2006-01-19
[QUOTE=cdean]I, too, am getting this same error.  I've gone over the configs probably three times now and can't figure it out.  I'm about 12 hours away from removing all the packages and configs and redoing it all from scratch.[/QUOTE]

what is your forward method details in the amavis conf
and what is your amavis settings in master.cf and the content_filter in main.cf ?

---

### Post by Stryker777 on 2006-01-19
I rechecked and rechecked, everything was there lol.  I then copied and pasted in the order that you had everything into my main.cf and it worked.  Didnt find a spelling error before but it works now so either I had a spelling error or the order of things listed is very important.  
Thanks again, have 3 running now based off your how-tos.  2 Breezy one hoary.
Laterz

---

### Post by jonesy on 2006-01-19
I'm having an issue authenticating outgoing email.  Everything else seems to be working, but SASL cannot authenticate against the database.  Nothing was showing up in the logs I was tailing until I noticed the following lines hidden in "auth.log".

> Jan 19 15:41:50 ns2 postfix/smtpd[26275]: SQL engine 'mysql ' not supported
Jan 19 15:41:50 ns2 postfix/smtpd[26275]: auxpropfunc error no mechanism available
Jan 19 15:41:50 ns2 postfix/smtpd[26275]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql


In "mail.log" I get the following message:

> Jan 19 15:43:42 ns2 postfix/smtpd[26297]: TLS connection established from unknown[192.168.100.181]: SSLv3 with cipher RC4-MD5 (128/128 bits)
Jan 19 15:43:45 ns2 postfix/smtpd[26297]: warning: unknown[192.168.100.181]: SASL LOGIN authentication failed
Jan 19 15:43:48 ns2 postfix/smtpd[26297]: warning: unknown[192.168.100.181]: SASL LOGIN authentication failed
Jan 19 15:43:48 ns2 postfix/smtpd[26297]: disconnect from unknown[192.168.100.181]


This is on a brand new install of Breezy.  Any ideas how to get this plugin to work?  I have installed every package listed on this howto.

---

### Post by jonesy on 2006-01-19
Nevermind, I should always heed warnings about trailing spaces . . .

Sorry.

---

### Post by peanut butter on 2006-01-24
i need help:
for some reason whenever i run Evolution as root@localhost it comes up with an error. and says authentication failed.
how do i set the password?im trying to login through imap if it helps

---

### Post by wannabelinuxconvert on 2006-01-31
Hi,

When I try and send an email locally (from the machine the servers running on) everything is fine and the mail gets delivered ...

```
Jan 31 20:56:19 localhost postfix/smtpd[9494]: connect from localhost.localdomain[127.0.0.1]
Jan 31 20:57:05 localhost postfix/smtpd[9494]: B8DCC40725: client=localhost.localdomain[127.0.0.1]
Jan 31 20:57:31 localhost postfix/cleanup[9499]: B8DCC40725: message-id=<20060131205647.B8DCC40725@ubuntu.dnsdojo.org>
Jan 31 20:57:31 localhost postfix/qmgr[9319]: B8DCC40725: from=<micpringle@hotmail.com>, size=400, nrcpt=1 (queue active)
Jan 31 20:57:31 localhost amavis[9245]: (09245-01) ESMTP::10024 /var/lib/amavis/tmp/amavis-20060131T205731-09245: <micpringle@hotmail.com> -> <xandros@lala.com> Received: SIZE=400 from ubuntu.dnsdojo.org ([127.0.0.1]) by localhost (ubuntu [127.0.0.1]) (amavisd-new, port 10024) with ESMTP id 09245-01 for <xandros@lala.com>; Tue, 31 Jan 2006 20:57:31 +0000 (GMT)
Jan 31 20:57:31 localhost amavis[9245]: (09245-01) Checking: <micpringle@hotmail.com> -> <xandros@lala.com>
Jan 31 20:57:31 localhost amavis[9245]: (09245-01) FWD via SMTP: [127.0.0.1]:10025 <micpringle@hotmail.com> -> <xandros@lala.com>
Jan 31 20:57:31 localhost postfix/smtpd[9503]: connect from localhost.localdomain[127.0.0.1]
Jan 31 20:57:31 localhost postfix/smtpd[9503]: 806E540728: client=localhost.localdomain[127.0.0.1]
Jan 31 20:57:31 localhost postfix/cleanup[9505]: 806E540728: message-id=<20060131205647.B8DCC40725@ubuntu.dnsdojo.org>
Jan 31 20:57:31 localhost postfix/qmgr[9319]: 806E540728: from=<micpringle@hotmail.com>, size=862, nrcpt=1 (queue active)
Jan 31 20:57:31 localhost postfix/smtpd[9503]: disconnect from localhost.localdomain[127.0.0.1]
Jan 31 20:57:31 localhost amavis[9245]: (09245-01) Passed, <micpringle@hotmail.com> -> <xandros@lala.com>, Message-ID: <20060131205647.B8DCC40725@ubuntu.dnsdojo.org>, Hits: -
Jan 31 20:57:31 localhost amavis[9245]: (09245-01) TIMING [total 350 ms] - SMTP EHLO: 4 (1%), SMTP pre-MAIL: 1 (0%), mkdir tempdir: 1 (0%), create email.txt: 1 (0%), SMTP pre-DATA-flush: 4 (1%), SMTP DATA: 38 (11%), body hash: 1 (0%), mkdir parts: 1 (0%), mime_decode: 13 (4%), get-file-type: 13 (4%), decompose_part: 2 (1%), parts: 0 (0%), AV-scan-1: 3 (1%), fwd-connect: 46 (13%), fwd-mail-from: 3 (1%), fwd-rcpt-to: 19 (5%), write-header: 3 (1%), fwd-data: 0 (0%), fwd-data-end: 193 (55%), fwd-rundown: 2 (0%), unlink-1-files: 5 (1%), rundown: 0 (0%)
Jan 31 20:57:31 localhost postfix/smtp[9500]: B8DCC40725: to=<xandros@lala.com>, relay=127.0.0.1[127.0.0.1], delay=44, status=sent (250 2.6.0 Ok, id=09245-01, from MTA: 250 Ok: queued as 806E540728)
Jan 31 20:57:31 localhost postfix/qmgr[9319]: B8DCC40725: removed
Jan 31 20:57:31 localhost postfix/virtual[9507]: 806E540728: to=<xandros@blobber.org>, orig_to=<xandros@lala.com>, relay=virtual, delay=0, status=sent (delivered to maildir)
Jan 31 20:57:31 localhost postfix/qmgr[9319]: 806E540728: removed
Jan 31 20:57:36 localhost postfix/smtpd[9494]: disconnect from localhost.localdomain[127.0.0.1]
```

But when I send from an external account, such as Hotmail, I get the following ...

```
Jan 31 21:11:01 localhost postfix/qmgr[9319]: 524E340715: from=<mic@hotmail.com>, size=385, nrcpt=1 (queue active)
Jan 31 21:11:02 localhost postfix/virtual[9534]: 524E340715: to=<mic@ubuntu.dnsdojo.org>, relay=virtual, delay=169820, status=sent (delivered to maildir)
Jan 31 21:11:02 localhost postfix/qmgr[9319]: 524E340715: removed
```

Which would suggest the mail has been delivered, but it's not in the maildir, nor has it seemed to have gone through all the checks of connecting locally ... any ideas !?

Mic

---

### Post by wannabelinuxconvert on 2006-01-31
I think it may have been the commented out fields in the rules file for shorewall, so I uncommented them all, but now it seems all mail is getting greylisted by postgrey, why is this !?

---

### Post by gimpologist on 2006-02-06
Wow...great "HowTo:" - I configured the entire mail server and got it up and running fairly painlessly and I'm a noob at linux. Thanks for it, cause it seems to be working like a charm.

So, I didn't get any errors in the logs (that I haven't fixed already) and all tests seem to be working flawlessly.  I've sent emails from other domains to the mailserver, sent emails from the mailserver and everything is being received and sent. But...

1)  Are there any wrap up details that I should go through to make sure that the server is good to go.  Any commented lines that need to be uncommented or vice versa.  Any logging that doesn't need to be logged? These types of things...etc.

2) Why is the syslog logging everything that mail.log logs?

_Friendly Suggestions for your "HowTo":_

1) In the postfix set-up of /etc/postfix/main.cf, you mention that you use your ISP as a relayhost.  You might want to add some more information on this as many ISP's require smtp authentication.  Mine does, so I added the following after finding some helpful info.

[INDENT]I added the following to main.cf after your "relayhost=" line:
```

smtp_sasl_auth_enable=yes
smtp_sasl_password_maps=hash:/etc/postfix/sasl_password
smtp_sasl_security_options=

```
Then, I created /etc/postfix/sasl_password file:
```

$ sudo nano /etc/postfix/sasl_password

```
Added the following text to the file:
```

#example
#smtp.comcast.com joeblow:whoknows
*my.smtphost.com* *username*:*password*

```
Made sure root owned the file:
```

$ sudo chown root:root /etc/postfix/sasl_password
$ sudo chmod 600 /etc/postfix/sasl_password

```
Ran this command and restarted postfix:
```

$ sudo postmap hash:/etc/postfix/sasl_password
$ sudo /etc/init.d/postfix restart

```[/INDENT]

2) You might consider going into more depth with POP3 since many people still require it as it fulfills it's purpose very well (which is to allow people to download their email from a central location and have the ability to read it off line). 

3) Some of the documentation gets a little hard to follow at some points when you're not explicitly stating what /path/file you are working on sometimes in your black command/code dialogs. I would say 95% understandable, but sometimes a little confusing for us noobs if you're not holding our hands even for a little bit.

Thanks again

---

### Post by flurdy on 2006-02-09
[QUOTE=peanut butter]i need help:
for some reason whenever i run Evolution as root@localhost it comes up with an error. and says authentication failed.
how do i set the password?im trying to login through imap if it helps[/QUOTE]

If you use the full howto and virtual domains, change the password for root@localhost in the users mysql database.
Otherewise if you are using a vanilla local installation then just change the root password. ie sudo passwd

---

### Post by flurdy on 2006-02-09
[QUOTE=gimpologist]
1)  Are there any wrap up details that I should go through to make sure that the server is good to go.  Any commented lines that need to be uncommented or vice versa.  Any logging that doesn't need to be logged? These types of things...etc.
[/QUOTE]

 Good idea, the test section(s) is mean to do this but I probably should fill them out more with a proper tidy up section etc. However each user will leave the server in a different state.

[QUOTE=gimpologist]

2) Why is the syslog logging everything that mail.log logs?
[/QUOTE]

Its annoying isnt it?
You can change it. There is a conf file somewhere that state what does not go into syslog. Cant remember where though, nor can I remeber which box I changed it on to replicate it....

[QUOTE=gimpologist]

_Friendly Suggestions for your "HowTo":_

1) In the postfix set-up of /etc/postfix/main.cf, you mention that you use your ISP as a relayhost.  You might want to add some more information on this as many ISP's require smtp authentication.  Mine does, so I added the following after finding some helpful info.

[/QUOTE]

Nice work. 
Hadnt thought of the ISP running authentication. 
Will have to add this ( with credit) to the howto.

[QUOTE=gimpologist]

2) You might consider going into more depth with POP3 since many people still require it as it fulfills it's purpose very well (which is to allow people to download their email from a central location and have the ability to read it off line). 
[/QUOTE]

I know, I just dont like POP myself. Most people use it out of ignorance of IMAP or lazyness. But yes it has its uses, with fetchmail etc and many, maybe even majority, people use it. Ps. Imap works offline as well if client supports it.
Not much need to be added anyway, so Ill have to add it one day.

[QUOTE=gimpologist]

3) Some of the documentation gets a little hard to follow at some points when you're not explicitly stating what /path/file you are working on sometimes in your black command/code dialogs. I would say 95% understandable, but sometimes a little confusing for us noobs if you're not holding our hands even for a little bit.

Thanks again[/QUOTE]

I know, Im not probably aware of where it is unclear. Dont want to make it too easy....

---

### Post by a2xm on 2006-02-09
Hi,

Thanks for the great how to. I'm a real newbie here and have this question.
On the create a .htaccess file in the phpMyAdmin setup:
> # either reuse an old .htpasswd file
# or as below , create one when you add the first user
htpasswd2 -c /path/to/htpasswd/file/outside/www/.htpasswd ausername
# then enter desired passwd
what do you meant by "/path/to/htpasswd/file/outside/www/.htpasswd"? may be you could give the example as well?

Thanks for your help.

:)

---

### Post by flurdy on 2006-02-09
[QUOTE=wannabelinuxconvert]I think it may have been the commented out fields in the rules file for shorewall, so I uncommented them all, but now it seems all mail is getting greylisted by postgrey, why is this !?[/QUOTE]

How was the emails already getting through the firewall before you uncommented the lines???

These two emails are for two different addresses (xandros@lala.com and [email]mic@ubuntu.dnsdojo.org[/email]) , hence not delivered to the same place?

All email will get greylisted one first attemp.

---

### Post by flurdy on 2006-02-09
[QUOTE=a2xm]Hi,

Thanks for the great how to. I'm a real newbie here and have this question.
On the create a .htaccess file in the phpMyAdmin setup:

what do you meant by "/path/to/htpasswd/file/outside/www/.htpasswd"? may be you could give the example as well?

Thanks for your help.

:)[/QUOTE]

"/path/to/htpasswd/file/outside/www/.htpasswd" is the path to wherever you choose to keep the htpasswd files. 
They should never be within a www folder. So /var/www is wrong or wherever your websites are contained.
So it it could be /etc/apache2/access or /var/apache2 or something.
Also you could possible have several htpasswd files for different purposes
so an example path could be 
"/etc/apache2/access/mysql.htpasswd" if you create the access  folder first.

---

### Post by a2xm on 2006-02-24
Hi Flurdy,

It's me again ;-) I just need some advices & confirmation that your howto can works on my situation.

I've an Internet sharing + firewall using IPCop ([http://ipcop.org](http://ipcop.org)) on my network's office. It's also works as the DNS & DHCP servers. Here's the quick fact:

Domain name: localdomain
IP address range: 192.168.1.200 - 192.168.1.220
Primary DNS: 192.168.1.1
Netmask: 255.255.255.0

And now I've another box (Ubuntu 5.10) that I want to make it as the mailserver. I've give it a static IP: 192.168.1.2 (fixed lease IP from DHCP) (btw, do I should make this as the Secondary DNS as well?).

I want this mailserver for my intranet. So emails from/to my domain (i.e. myoffice.com) doesn't have to go to the Internet. Which is I can save a lot of bandwidth. And of course, emails to all others domains (i.e. yahoo.com, gmail.com, etc.) will forwarded to the ISP's SMTP.

OK, I think that all is my situation here. Any kind of suggestion & helps would be really appreciated. Many thanks.. :) 

cheers,
a2xm

---

### Post by cdean on 2006-02-24
[QUOTE=flurdy]what is your forward method details in the amavis conf
and what is your amavis settings in master.cf and the content_filter in main.cf ?[/QUOTE]

Wow, do I feel stupid.  It ended up being a typographical error on the 127.0.0.1:10025 line of master.cf.  I had "smtp" instead of "smtpd".  At least I found it myself with no one around ;)

---

### Post by diebels on 2006-03-01
Hi! Great howto, my server is running fine.

Now I'd like to set up aliases with multiple recipients.

I want mail to the alias 'everyone@mydomain.com' be forwarded to both 'kari@mydomain.com' and 'ola@mydomain.com'.

How would I do that? procmail? mailman?

---

### Post by pradtf on 2006-03-04
[QUOTE=Zandaa]what are my DNS MX records??? I've never heard anything about those :confused: :confused: :confused:[/QUOTE]

i believe they are what you set up in your zone files.
for instance, if you go to [www.dnsstuff.com](www.dnsstuff.com) and enter flurdy.com in the DNS Lookup Box choosing MX (rather than the default A), you see:

flurdy.com.  MX  IN  86400  smtp.firefix.org. [Preference = 20]
flurdy.com.  MX  IN  86400  smtp.flurdy.net. [Preference = 30]
flurdy.com.  MX  IN  86400  newby.dyndns.org. [Preference = 40]

which are the records that are in the zone files for that domain and are used by nameservers.

what i don't understand is if you are hosting multiple virtual domains, which one should you put in or should you just make something up?

---

### Post by pradtf on 2006-03-04
[QUOTE=vtec]A while back i set up a simple mail server, and did not use mySQL. Could someone tell me what is stored in the database they are setting up and why its a better to use then not??[/QUOTE]

you store the same stuff in mysql that you would in the textfiles, but whenever you make a change you have to do a conversion into a .db file (eg with sendmail it is postmap hash whatever < whatever).

so among several other issues, one of the real benefits is that you don't even have to manage alterations and can leave this to your users with a php script that inserts into the database. for instance, if you wanted to add a forward 

[email]me@here.com[/email] ------- [email]you@where.com[/email]

you just put it into the db and that's that!

---

### Post by pradtf on 2006-03-04
great howto flurdy! 
everything is working fine except the amavis stuff for me. 
if i put in either 
amavis unix - - - - 2 smtp 
-o smtp_data_done_timeout=1200 
-o smtp_send_xforward_command=yes, 
postfix refuses to start 
or even 
-o cleanup_service_name=pre-cleanup (under smtp inet n - - - - smtpd) 
postfix refuses to distribute the mail. 

the log report says: Mar 4 16:55:25 ns2 postfix/qmgr[13292]: warning: connect to transport amavis: Connection refused which is rather uncooperative, but i don't see why that would cause postfix to crash.

edit: 
ok the crashing problem is solved! 
the -o lines must have some whitespace in front or it won't work (i was just copying and pasting)

now to see why amavis is causing the log to print:
Error in processing, id=07414-03, creating_partsdir FAILED: SQL server(s) not reachable at (eval 41) line 198, <GEN13> line 17

---

### Post by mattcole on 2006-03-24
Wow, that's a huge amount of material flurdy, thanks a lot for putting that together.

I have gotten all the way through to the squirrelmail installation, which was actually the only part that I was truly interested in, when I got confused.  Specifically, which user/pw are we looking for when running the squirrelmail config script, which you've called out as :

**mysql://username: password@127.0.0.1/database**

Root?  Mail?  A new squirrlemail account?  My user acct?

Can anyone cure my brain damage?

TIA,
Matt

---

### Post by peanut butter on 2006-03-24
[QUOTE=mattcole]Wow, that's a huge amount of material flurdy, thanks a lot for putting that together.

I have gotten all the way through to the squirrelmail installation, which was actually the only part that I was truly interested in, when I got confused.  Specifically, which user/pw are we looking for when running the squirrelmail config script, which you've called out as :

**mysql://username: password@127.0.0.1/database**

Root?  Mail?  A new squirrlemail account?  My user acct?

Can anyone cure my brain damage?

TIA,
Matt[/QUOTE]

i dont think it matters which account althoe it might be a good idea to use root.:)

---

### Post by slyons on 2006-03-30
hi flurdy,

you're guide is really amazing!  i am so close to having this setup.  i can send to local addresses, but i cannot seem to send to any non-local email address.  here is the output from my mail.log.  please help!

Mar 30 08:43:46 localhost postfix/smtp[19578]: 93328FB983: to=<XXX@YYY.com>, relay=none, delay=59632, status=deferred (Host or domain name not found. Name service error for name=YYY.com type=MX: Host not found, try again)

also, when i go to dnsstuff.com, it says that there are no MX records for my domain.

---

### Post by usulsuspct on 2006-04-01
Okay...I am down to my last strand of hair.

I have followed the direx (best I can at least, and am having a problem I cant seem to lick.)  Currently the IMAP portion seems to work, I can connect up and view folders...postfix receipt of mail seems to be working (I have only performed local test.)

My issue is with SASL authentication.  I get prompted to accept certificate however entering my password gets me know where.  I can see it cycle through the auth methods but none work.  If I look in the log this is what I find:

mail.log

```

Apr  1 10:07:20 localhost postfix/smtpd[16471]: warning: SASL authentication failure: no secret in database
Apr  1 10:07:20 localhost postfix/smtpd[16471]: warning: unknown[192.168.16.66]: SASL CRAM-MD5 authentication failed
Apr  1 10:07:20 localhost postfix/smtpd[16471]: warning: SASL authentication failure: Password verification failed
Apr  1 10:07:20 localhost postfix/smtpd[16471]: warning: unknown[192.168.16.66]: SASL PLAIN authentication failed
Apr  1 10:07:20 localhost postfix/smtpd[16471]: warning: unknown[192.168.16.66]: SASL LOGIN authentication failed
Apr  1 10:07:24 localhost postfix/smtpd[16471]: warning: SASL authentication failure: no secret in database
Apr  1 10:07:24 localhost postfix/smtpd[16471]: warning: unknown[192.168.16.66]: SASL CRAM-MD5 authentication failed
Apr  1 10:07:25 localhost postfix/smtpd[16471]: warning: SASL authentication failure: Password verification failed
Apr  1 10:07:25 localhost postfix/smtpd[16471]: warning: unknown[192.168.16.66]: SASL PLAIN authentication failed
Apr  1 10:07:28 localhost postfix/smtpd[16471]: warning: unknown[192.168.16.66]: SASL LOGIN authentication failed

```

I have checked and re-checked my settings and I cant find anything that looks out of place.  Below is my /etc/postfix/sasl/smtpd.conf:

```

pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: *****
sql_passwd: *******
sql_database: maildb
sql_select: select clear from users where id='%u@%r' and enabled = 1

```

I have manually run the query with what I think gets substitued for the id and it returns the password.  I have the mysql log turned on however I dont see any sign of this query every getting run.

Here is my main.cf if it helps any:

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/postfix/postfix.cert
smtpd_tls_key_file = /etc/postfix/postfix.key
smtpd_data_restrictions = reject_unauth_pipelining

content_filter = amavis:[127.0.0.1]:10024
#receieve_override_options = no_address_mappings

#adding the postgrey policy:
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks,
        reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination,
        check_policy_service inet:127.0.0.1:60000, permit

# modify the existing smtpd_recipient_restrictions
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks,
        permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination,
        check_policy_service inet:127.0.0.1:60000, permit

# modify the existing smtpd_sender_restrictions
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender,
        reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes

smtpd_sasl_path = /etc/postfix/sasl/smtpd.conf:/usr/lib/sasl2

smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

POSTGREY_OPTS="--inet=127.0.0.1:60000 --delay=60" #POSTGREY_TEXT="Your customized rejection message here"

myhostname = usulsuspct.homelinux.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
relayhost = smtp-server.stny.rr.com
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host

masquerade_domains = jstuart.net !usulsuspct.homelinux.com
masquerade_exceptions = root

local_recipient_maps =
mydestination =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h

# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450

# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d

# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s

# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s

# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16

# how many error before back off.
smtpd_soft_error_limit = 3

# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,
        reject_invalid_hostname, permit

# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender,
        reject_unknown_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client relays.ordb.org,
        reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

# Requirement for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient,
        reject_unknown_recipient_domain, reject_unauth_destination, permit

# require proper helo at connections
smtpd_helo_required = yes

# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases

# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual

# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf

# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf

# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf

# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf

# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

```

I am not sure what else to try, anyone out there have some advice for me?

Thanks in advance...

---

### Post by diebels on 2006-04-01
Using [email]user@domain.tld[/email] as login?
Using tls connection? I could not get ssl running, only tls.

---

### Post by usulsuspct on 2006-04-01
I got my setup working...oversite in my setup.  I will say though spending a few hours banging head off the setup I learned a lot more about it.

---

### Post by wannabelinuxconvert on 2006-04-04
Hey Flurdy,

Fantastic doc ... really works a treat.

Just a suggestion, but have you thought about adding in details for soft quota for the mailbox's as described here 

[Postfix Soft Quota Support]("http://brunny.com/content/view/9/50/")

I think this would be a really good addition to the info you've created (*Plus it'd really help me because I need this but still considering myself a newbie I don't want to wreck the current setup*)

Cheers

Mic

---

### Post by dcollamore on 2006-04-11
Here's a quickie: I managed to get the whole setup working, with a little effort, but I notice the HOWTO doesn't include anything about auto-magically creating the user directories in /var/spool/mail/virtual.  Is it supposed to do that and I have something misconfigured, or is that a manual thing?  I have no problems with my setup once I manually create /var/spool/mail/virtual/'user' and the appropriate tmp, cur, and new folders and chowning them to virtual...Thinking about whipping up a quick little 'add user' script to automate the thing as a matter of fact...just wondering if I've overlooked something.  Thanks!

--Edit--
BTW, great howto!

---

### Post by flurdy on 2006-04-12
How to create user directory is a frequent question, and probably asked many times already in this thread.

There are scripts that do it, and some work fine, but I recommend not to use them. 

Basically if your set up is correct then the postfix will create the folders. However it will only create them when it receives its first email for that user!!!!!!

So if the folders dont exist, then there has not been an email for that user yet.
So simply send one to that user. 

Still no folders? Then your postfix is misconfigured. No point manually creating them, fix your postfix instead.

---

### Post by flurdy on 2006-04-12
[QUOTE=wannabelinuxconvert]Hey Flurdy,

Fantastic doc ... really works a treat.

Just a suggestion, but have you thought about adding in details for soft quota for the mailbox's as described here 

[Postfix Soft Quota Support]("http://brunny.com/content/view/9/50/")

I think this would be a really good addition to the info you've created (*Plus it'd really help me because I need this but still considering myself a newbie I don't want to wreck the current setup*)

Cheers

Mic[/QUOTE]


Quota is something I have been planning to include but never gotten round to. The tables and courier etc is set up for it, but never done any further.

If the one you mention does work, then Ill link to it? Anyone else with some experience with this?

---

### Post by dcollamore on 2006-04-12
[QUOTE=flurdy]How to create user directory is a frequent question, and probably asked many times already in this thread.

There are scripts that do it, and some work fine, but I recommend not to use them. 

Basically if your set up is correct then the postfix will create the folders. However it will only create them when it receives its first email for that user!!!!!!

So if the folders dont exist, then there has not been an email for that user yet.
So simply send one to that user. 

Still no folders? Then your postfix is misconfigured. No point manually creating them, fix your postfix instead.[/QUOTE]

Of course, I missed that little gem...Postfix is indeed working fine as a newly created test user's mail folders *are* created on first mail.  My bad on that one...thanks for your timely response to a foolish question! ](*,)

---

### Post by widjajayd on 2006-04-16
hai, I am a newbie

I have tried setup and follow these intructions,
and have some questions:

1. I would like to setup local email server only for my LAN,
for example 5 pcs, all with ubuntu breezy (ip address 192.168.0.1 - 5)
do I have to setup local DNS server for this, 

2. some of instruction asked me to rename mydomain and myhostname
consider I am using LAN not internet what I should change for mydomain and myhostname ?
(my network only use pc name: ws01 - ws05)

Thanks before.

---

### Post by marco_milano on 2006-04-30
Please can you give me hints how to add fetchmail to get mails from public server? I want use this as internal company server, with more internal user than public ones ( with e-mails on ISP).
I would use fm to:
Get emails via pop from ISP
give them to proper local user
have fm running as a service every 5 minutes

Thanks for the help ( my knowhow on linux is about null...)

---

### Post by Tortanick on 2006-05-01
I have a question, useing your guide is it possible to get spam and virusus to arrive at their intended destination but with a custom message added to the subject field? (diffrent message for each)

I'm aiming for zero false positives

---

### Post by Tortanick on 2006-05-01
never mind, I figured it out myself.

However something else coame up, I'm trying to add POP to my server and I reached the stage whre cyrus SASL needs to be isntalled, spasifically the line:

"If you need Pop, modify the pop file as well" I'm not sure what to do to the pop file.

---

### Post by trawler on 2006-05-01
Flurdy, Just thought you should know - 
Your guide, is BY FAR the most extensive one i've read online. My server was running perfectly, and it's all thanks to you :D.

Really, good job :)

And since i'm working for an ISP i often come across people who are interested in setting up their own mail servers - and i always, but always, refer them to your site.
Last saturday, when your site was down (or was it friday? :)), I even got a call from a panicky friend who needed it badly :D

So, again, thanks :D

---

### Post by flurdy on 2006-05-02
[QUOTE=trawler]Flurdy, Just thought you should know - 
Your guide, is BY FAR the most extensive one i've read online. My server was running perfectly, and it's all thanks to you :D.

Really, good job :)

And since i'm working for an ISP i often come across people who are interested in setting up their own mail servers - and i always, but always, refer them to your site.
Last saturday, when your site was down (or was it friday? :)), I even got a call from a panicky friend who needed it badly :D

So, again, thanks :D[/QUOTE]

Cheers. 
:cool: 

Bit greedy to take all the credit, its after all an collection of knowledge from other people's howtos, articles and experience into a server and doc that works for me.

Ps. the server is up and down because the ISP where it is hosted is suffering from denial of service attacks. (or at least that is the excuse...) Cant complain, my servers are there for free in my employers rack.

The google cache version of works.

---

### Post by giorg on 2006-05-03
[QUOTE=flurdy]Cheers. 
:cool: 

Bit greedy to take all the credit, its after all an collection of knowledge from other people's howtos, articles and experience into a server and doc that works for me.

Ps. the server is up and down because the ISP where it is hosted is suffering from denial of service attacks. (or at least that is the excuse...) Cant complain, my servers are there for free in my employers rack.

The google cache version of works.[/QUOTE]

Hi,
I have everything working and no errors in the logs, but it seems amavis doesn't check for spam. Shouldn't I have the X-SPAM header into every email?
Thx Andrea

---

### Post by Acker on 2006-05-04
Hi!

Thanks for the great work. I have a problem concerning amavisd-new.
At my server there ist no amavisd.conf. It seems that the files have been split in the folder conf.d but i dont find the required options for the howto...

Can someone help me please!?

Greetz,
Acker

---

### Post by trawler on 2006-05-04
Hi flurdy,
I've set up a mail server before, on ubuntu 5.10 (breezy) and didn't have much of a problem with it.
The problem is, that a few days ago, i decided to go and upgrade to Dapper Drake.

I know your guide reffers to Breezy, but I figured I'll give it a try.
Well.. I *think* something is wrong with courier (not sure).
And the reson I'm not sure, is that mail.info and/or mail.log don't show anything... (never happened to me before).

So basically, I've got a few problems - 
1) unable to log into the mailbox using a mail program (thunderbird) (didn't install squirrelmail yet).
2) mysql.log shows queries being perfomed, but can't see any activity in mail.info/mail.log (I'm used to seeing connections activity, login attempts, but this time nada).
3) I could see (via webmin) that postfix stored incoming messages in /var/mail/*user* instead of /var/spool/mail/virtual/*user*.

I suppose I could manage troubleshooting all of these, If I could only see the debugging logs! That is my main concern.
I thought it could have something to do with the different package versions (deffinetly for amavis, since i had to downgrade to the breezy version), but I can't know for sure.

As for the configuration - I checked anywhere I could think of, according to your guide, to see where I might have left debugging off, but it's all on.

btw - the servers are up (although the ports are currently closed to outside connections).
telnet localhost 25 and telnet localhost 143 respond well, and again - can't see any trace of the connection being made while tail -f /var/log/mail.info or /var/log/mail.log.

Any idea why? this is very annoying. I even considered downgrading all of the packaged to recent breezy versions, and i guess i will, if i can't find a different solution...


Please help!

---

### Post by kkimmell on 2006-05-04
Never mind... found it and couldn't figure out how to delete the post.

---

### Post by kkimmell on 2006-05-04
[QUOTE=Tortanick]I'm trying to add POP to my server and I reached the stage whre cyrus SASL needs to be isntalled, spasifically the line:

"If you need Pop, modify the pop file as well" I'm not sure what to do to the pop file.[/QUOTE]

I'm stuck at this same place and I didn't see an answer to your query. Have you, by chance, figured it out?

I see several POP3AUTH type lines in the POP3d file but none that match up to the "IMAP_CAPABILITY" setting that was referred to. I guessed that perhaps it would be POP3_Capability but of course that's not it.

-K

---

### Post by Tortanick on 2006-05-04
No I havn't figured it out, sorry.

---

### Post by prixar on 2006-05-09
[QUOTE=diebels]Hi! Great howto, my server is running fine.

Now I'd like to set up aliases with multiple recipients.

I want mail to the alias 'everyone@mydomain.com' be forwarded to both 'kari@mydomain.com' and 'ola@mydomain.com'.

How would I do that? procmail? mailman?[/QUOTE]

Hi,
I have the same problem, everything works fine, but I want create aliases with multiple recipients too. Did you solve this problem???

Thanx.

---

### Post by flurdy on 2006-05-10
[QUOTE=prixar]Hi,
I have the same problem, everything works fine, but I want create aliases with multiple recipients too. Did you solve this problem???

Thanx.[/QUOTE]

look in the mail list section.

basically just seperate them with a comma in the mail destination.

---

### Post by kkimmell on 2006-05-12
My SMTP and IMAP tests have passed on the local machine but now that I've opened the ports up to test from an external source I get connection failed messages. My SHOREWALL config is as follows:

AllowPing		loc	fw 
AllowSSH		loc	fw 
AllowSMTP		loc	fw 
ACCEPT		loc	fw	tcp	465,587 -
AllowIMAP		loc	fw
AllowWeb		loc	fw

AllowPing		net	fw 
AllowSSH		loc	fw 
AllowWeb		net	fw
**[COLOR="Red"]AllowSMTP		net	fw [/COLOR]**
ACCEPT		net	fw	tcp 465,587 - 
AllowIMAP		net	fw

Shouldn't the highlighted line be allowing me access? And yes I've restarted shorewall and I've even rebooted the machine. Postfix is running as I can connect if I telnet from the local machine.

Help? ](*,)

---

### Post by prixar on 2006-05-13
Hi,
Anyone have solution, how can I import SMTP and POP certificate to MS Outlook or Outlok express? Because everytime when client start MS Outlook, popup warning "The server you are connected is using a security certificate that could not be verified" and I must click YES...For a while its ok but when I close MS Outlook and start it again, that message popup again...

Thanx

---

### Post by Tortanick on 2006-05-13
I'd have thought could not be verified would mean that the certificate was not from a truseted authority like verisign. But I can't say I know for sure.

Flurdy, I have a few questions: 
1) if I wanted to put my mail in its own partition: /mail could I change the line virtual_mailbox_base so it says /mail/spool/mail/virtual instead of /var/spool/mail/virtual in postfix's main.cf or would that cause problems elsewhere?

2) any plans to update for dapper drake?

3) would you mind if I ported the guide to the ubuntu wiki? That way people could add their own little add ons to the guide, I myself have allready written a guide for SQLgrey (looks better than postgrey) although I can't say I'm confident I got it right.

P.S. If you don't want it on the ubuntu wiki I'd happily give you any add-ons I write.

---

### Post by rklauco on 2006-05-13
[QUOTE=Acker]Hi!

Thanks for the great work. I have a problem concerning amavisd-new.
At my server there ist no amavisd.conf. It seems that the files have been split in the folder conf.d but i dont find the required options for the howto...

Can someone help me please!?

Greetz,
Acker[/QUOTE]
Acker, did you solve it somehow?
I got to the same point with latest dapper - no amavisd.conf file created...

---

### Post by prixar on 2006-05-14
[QUOTE=Tortanick]I'd have thought could not be verified would mean that the certificate was not from a truseted authority like verisign. But I can't say I know for sure.
[/QUOTE]

Yes its not trusted authority, but Thunderbird give me choice "Accept this certificate permanently" and its ok. But in Outlook I dont know how can I accept it permanently....

---

### Post by prixar on 2006-05-15
I have a little problem with Postgrey..maybe..??!!


May 15 12:56:42 mail postfix/smtpd[19420]: NOQUEUE: reject: RCPT from smtp-out4.iol.cz[194.228.2.92]: 450 <xxxx@yyyyy.sk>: Recipient address rejected: Greylisted for 60 seconds (see [http://isg.ee.ethz.ch/tools/postgrey/help/yyyyy.sk.html);](http://isg.ee.ethz.ch/tools/postgrey/help/yyyyy.sk.html);) from=<poprovsky@helukabely.cz> to=<xxxx@yyyyy.sk> proto=SMTP helo=<smtp-out4.iol.cz>

That email [email]xxxx@yyyyy.sk[/email] is alias, original email is different. Maybe is incorect check in aliases?? That email arive after 25 min.....But some users tell me that many emails dont arrive....?? Why is that email for my regular alias rejected??

---

### Post by und3rtug4 on 2006-05-18
I had followed the guide mencioned in the begining of the topic, and everything seens to works just fine, except that I cant send any email to any external account (*@gmail.com, *@hotmail.com, *@whatever.com)!!!

Can anyone help me explaining what i did wrong or needs to be done!?

Thanks in advance!

---

### Post by Slicer101 on 2006-05-24
Anyone tried to get this setup to work with Dapper? 

Only a few days left until the release, so it would be nice to be able to use this great guide on the latest release. I have seen a few issues where some files are no longer present. One that comes to mind is amavid.conf.](*,) 

Thanks!

Slicer

---

### Post by Flintz on 2006-05-24
Hi there, I am posting here cause I used this howto to install a mailserver on my debian system, but something is not running correctly, so I hoped you could help me :)
I followed the howto exactly, I only left out everything that has to do with spamfiltering etc.

The problem I have is, that I cannot connect to the server to check my mail, my mailprogram always says "Connecting..." for a few seconds and then "login failed" (tried with several mailprogramms, ssl activated and disabled just to be sure).

Here are some logfiles:
/var/log/mail.info
```
May 24 21:34:53 vs2054 imapd-ssl: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], command=CAPABILITY
May 24 21:34:53 vs2054 imapd-ssl: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], command=LOGIN
May 24 21:34:53 vs2054 imapd-ssl: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], username=test
May 24 21:34:53 vs2054 imapd-ssl: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], password=*****
May 24 21:34:58 vs2054 imapd-ssl: LOGIN FAILED, ip=[::ffff:84.148.98.2]
May 24 21:34:59 vs2054 imapd-ssl: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], command=LOGOUT
May 24 21:34:59 vs2054 imapd-ssl: LOGOUT, ip=[::ffff:84.148.98.2]
May 24 21:39:44 vs2054 imaplogin: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], command=CAPABILITY
May 24 21:39:44 vs2054 imaplogin: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], command=LOGIN
May 24 21:39:44 vs2054 imaplogin: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], username=test
May 24 21:39:44 vs2054 imaplogin: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], password=*****
May 24 21:39:49 vs2054 imaplogin: LOGIN FAILED, ip=[::ffff:84.148.98.2]
May 24 21:39:50 vs2054 imaplogin: LOGIN: DEBUG: ip=[::ffff:84.148.98.2], command=LOGOUT
May 24 21:39:50 vs2054 imaplogin: LOGOUT, ip=[::ffff:84.148.98.2]
```

vs2054 is the machine's name and test is obviously a testuser I created :)
A little excerpt from the /var/log/mysql/mysql.log although everything looks quite ok to me

```
060524 21:33:12     258 Connect     mail@localhost on maildb
                    258 Query       select destination from aliases where mail = 'gmx.net' and enabled = 1
                    259 Connect     mail@localhost on maildb
                    259 Query       select domain from domains where domain = 'gmx.net' and enabled = 1
060524 21:33:24     258 Query       select destination from aliases where mail = 'missingmatter.de' and enabled = 1
                    259 Query       select domain from domains where domain = 'missingmatter.de' and enabled = 1
                    260 Connect     mail@localhost on maildb
                    260 Query       select destination from aliases where mail = 'test@missingmatter.de' and enabled = 1
                    261 Connect     mail@localhost on maildb
                    261 Query       select destination from aliases where mail = 'test@missingmatter.de' and enabled = 1
060524 21:33:33     262 Connect     mail@localhost on maildb
                    262 Query       select maildir from users where id = 'test@missingmatter.de' and enabled = 1
                    263 Connect     mail@localhost on maildb
                    263 Query       select uid from users where id = 'test@missingmatter.de'
                    264 Connect     mail@localhost on maildb
                    264 Query       select gid from users where id = 'test@missingmatter.de'
060524 21:34:24     258 Quit
                    259 Quit
                    261 Quit
060524 21:34:33     262 Quit
                    263 Quit
                    264 Quit
060524 21:35:35     260 Quit

```

missingmatter.de is the domain where the mailserver is running on.
So I tried the the test-part of the howto, I telnetted to localhost:25 and send a mail to [email]test@missingmatter.de[/email], and looked into /var/spool/mail/virtual and the directory "test" was created (just like I defined in the mysql database) and the mail was there, also /var/log/mail said it was delivered:
```
May 24 21:33:33 vs2054 postfix/qmgr[12998]: 459E24DB7: from=<flintz@gmx.net>, size=384, nrcpt=1 (queue active)
May 24 21:33:33 vs2054 postfix/virtual[23309]: 459E24DB7: to=<test@missingmatter.de>, relay=virtual, delay=21, status=sent (delivered to maildir)

```

Somehow this error appears sometimes on the mail.info, but I cant really find out why:
```
May 24 22:02:27 vs2054 postfix/smtpd[24515]: connect from mail.gmx.net[213.165.64.20]
May 24 22:02:27 vs2054 postfix/smtpd[24515]: warning: connect to 127.0.0.1:60000: Connection refused
May 24 22:02:27 vs2054 postfix/smtpd[24515]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May 24 22:02:28 vs2054 postfix/smtpd[24515]: warning: connect to 127.0.0.1:60000: Connection refused
May 24 22:02:28 vs2054 postfix/smtpd[24515]: warning: problem talking to server 127.0.0.1:60000: Connection refused
May 24 22:02:28 vs2054 postfix/smtpd[24515]: NOQUEUE: reject: RCPT from mail.gmx.net[213.165.64.20]: 450 Server configuration problem; from=<flintz@gmx.net> to=<test@missingmatter.de> proto=SMTP helo=<mail.gmx.net>
May 24 22:02:28 vs2054 postfix/smtpd[24515]: disconnect from mail.gmx.net[213.165.64.20]

```

When I telnet to localhost 143 I get this:
```
vs2054:/etc/postfix# telnet localhost 143
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4rev1 UIDPLUS CHILDREN NAMESPACE THREAD=ORDEREDSUBJECT THREAD=REFERENCES SORT QUOTA AUTH=CRAM-MD5 AUTH=CRAM-SHA1 IDLE ACL ACL2=UNION STARTTLS] Courier-IMAP ready. Copyright 1998-2004 Double Precision, Inc.  See COPYING for distribution information.

```

Btw, why do I have to connect to 143 when I want ssl-encrypted connection? I thought imap-ssl uses 993?

I think I have a problem with the audaemon from courier, but I am not sure...I also have no idea how to track down the problem more. Postfix doesn't seem to be the source as it worked with the telnet try, mysql seems also to work, cause the mail was delivered to the correct maildir in /var/spool/mail/virtual.

Any ideas are highly appreciated :)

---

### Post by Flintz on 2006-05-24
Ok, forget the issue where it says it can't connect to 127.0.0.1:60000 I found out that I forgot to remove this from the postfix main.cf as I don't use postgrey.
I sent a testemail to test(at)missingmatter.de which was correctly received and delivered to the maildir.

Logging in via courier-imap still doesn't work though.
I use sylpheed-claws to test the account, I used this settings, maybe there is an error?
imap-server: vs2054.missingmatter.de
smtp: vs2054.missingmatter.de
user: test(at)missingmatter.de
password: guess what? I entered the password ;)
SSL for IMAP4 and SMTP is activated.

Well I am making some progress here, but the most important part is still missing: being able to actually read my mails ;)

---

### Post by lex1 on 2006-05-25
Can somone please tell the line in main.cf and master cf for useing tls BUT not with smtp auth.


the line below are from the howto but do i just delete the smtp auth section?

# these may already be present in your file, # however I usually have to add them # also, this specific line used to use fifo, it now needs to use unix type tlsmgr unix - - n 300 1 tlsmgr smtps inet n - n - - smtpd -o smtpd_tls_wrappermode=yes -o smtpd_sasl_auth_enable=yes 587 inet n - n - - smtpd -o smtpd_enforce_tls=yes -o smtpd_sasl_auth_enable=yes

this line givesme some confusion in the postfix main.cf file
how does it appy i my case?

smtpd_use_tls = yes smtpd_tls_cert_file = /etc/postfix/postfix.cert smtpd_tls_key_file = /etc/postfix/postfix.key smtpd_data_restrictions = reject_unauth_pipelining



does the tls config look ok below any sugesstions for improvements please>



smtpd_use_tls = yes
> > > >  smtp_use_tls = yes
> > > >  smtp_tls_note_starttls_offer = yes
> > > >  smtpd_tls_auth_only = yes
> > > >  smtpd_tls_key_file = /etc/postfix/tls/xstation_sav.net_req.pem
> > > >  smtpd_tls_cert_file = /etc/postfix/tls/xstation_sav.net_cert.pem
> > > >  smtpd_tls_CAfile = /etc/postfix/tls/cacert.pem
> > > >  smtpd_tls_loglevel = 1
> > > >  smtpd_tls_received_header = yes
> > > >  smtpd_tls_session_cache_timeout = 3600s


lex1

---

### Post by flurdy on 2006-06-01
[QUOTE=lex1]Can somone please tell the line in main.cf and master cf for useing tls BUT not with smtp auth.

lex1[/QUOTE]

lex1, please dont post here, PM and email me. One will do, preferably just post in this thread. I simply cant reply to every message, especially when im not sure of the solution (or question). 

My guess is that you want TLS security but not SASL authentication? Just remove all references to SASL?

---

### Post by flurdy on 2006-06-02
[QUOTE=Tortanick]I'd have thought could not be verified would mean that the certificate was not from a truseted authority like verisign. But I can't say I know for sure.

Flurdy, I have a few questions: 
1) if I wanted to put my mail in its own partition: /mail could I change the line virtual_mailbox_base so it says /mail/spool/mail/virtual instead of /var/spool/mail/virtual in postfix's main.cf or would that cause problems elsewhere?
[/QUOTE]

The home field in the users table needs to beupdated as well.

> 
2) any plans to update for dapper drake?


Yes, started it. Also a new thread for dapper specific questions

> 
3) would you mind if I ported the guide to the ubuntu wiki? That way people could add their own little add ons to the guide, I myself have allready written a guide for SQLgrey (looks better than postgrey) although I can't say I'm confident I got it right.

P.S. If you don't want it on the ubuntu wiki I'd happily give you any add-ons I write.

There are already alternatives in the wiki made by others using slightly different packages and methods. However If you write any add ons, I will happily link to it.

---

### Post by flurdy on 2006-06-02
[QUOTE=rklauco]Acker, did you solve it somehow?
I got to the same point with latest dapper - no amavisd.conf file created...[/QUOTE]

amavisd conf is split into several files.
thankfully there is a quick work around. 

simple put the specific changes into a new 50users file in /etc/amavisd/conf.d

See the new debian thread and the updated 5th edition of the howto

---

### Post by flurdy on 2006-06-02
[QUOTE=und3rtug4]I had followed the guide mencioned in the begining of the topic, and everything seens to works just fine, except that I cant send any email to any external account (*@gmail.com, *@hotmail.com, *@whatever.com)!!!

Can anyone help me explaining what i did wrong or needs to be done!?

Thanks in advance![/QUOTE]

Is that sending as normal smtp sending or aliasing to external accounts?

You may need to review your main.cf and look a the
inet_interfaces
smtpd_recipient_restrictions

is it the sender, client or recipient it doesnt like?

---

### Post by cconk01 on 2006-06-07
I think i have gotten pretty far setting up the email, but i went to the test page and i have recieved this error message: 
>     ERROR: Required PHP PEAR DB support is not available. Is PEAR installed and is the include path set correctly to find DB.php? The include path is now: ".:/usr/share/php:/usr/share/pear".

then when i try to log in with my root username i get these error messages
> 
Warning: include_once(DB.php) [function.include-once]: failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: include_once() [function.include]: Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/squirrelmail/functions/db_prefs.php on line 40
ERROR:
Could not include PEAR database functions required for the database backend.
Is PEAR installed, and is the include path set correctly to find DB.php?
Please contact your system administrator and report this error.

What have i done wrong?

---

### Post by GlennB on 2006-06-28
First, thanks for a great howto! 

I'm having a small problem understanding one part of the Squirrelmail configuration though.

While running the conf.pl file to configure Squirrelmail, the howto says to enter 9, then 1, to get to the DSN setup. Ok so far, but then it asks to enter

```
mysql://usename:password@127.0.0.1/database
```

Being a mysql newbie, I can't work out if I should type that line literally, or (more likely) if I should substitute my own values. If so, which username, password and database name should I be using? ](*,) 

I must have missed something simple, but trawling the docs and forums hasn't got me anywhere. Any clues??

---

### Post by cconk01 on 2006-06-29
WOW! that was the second go round for me. Being a newbie at all this i think i have done alright for myself. I think/guess this isnt to big a problem to fix but whenever i try to log into squirrelmail via http I get [HTML]ERROR: Connection dropped by IMAP server.
[/HTML]

With your extreme knowledge in this subject im guessing you would know whats going on?

---

### Post by RShadow on 2006-06-30
I am running into a small problem.  Whenever I try to auth to check mail the login fails.  I have verified that the password that is being send and the password stored in the mysql database match, so I can't figure out why it is failing.

However I have noticed the following in my logs
```

Jun 30 07:24:52 zues imaplogin: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Jun 30 07:24:52 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], command=CAPABILITY
Jun 30 07:24:53 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], command=LOGIN
Jun 30 07:24:53 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], username=user@domain
Jun 30 07:24:53 zues imaplogin: LOGIN: DEBUG: ip=[::ffff:xxx.xxx.xxx.xxx], password=cleartextpass
Jun 30 07:24:53 zues imaplogin: authdaemon: starting client module
Jun 30 07:24:53 zues imaplogin: authdaemon: TEMPFAIL - no more modules will be tried
Jun 30 07:24:58 zues imaplogin: LOGIN FAILED, ip=[::ffff:xxx.xxx.xxx.xxx]

```
stripped IP's and acutal domains/passwords/users.. any ideas what is wrong with my setup?

---

### Post by herald on 2006-06-30
UPDATE: Please ignore this, I've found the Dapper Drake thread for this HOWTO.  Sorry!

Question about this (fabulously thorough) HOWTO on Ubunto 6.06 Dapper Drake:

I'm finding that several of the packages mentioned in the HOWTO are not available...one example would be "courier-authmysql" the spamassasin and a few others.  I expect that the spamassassin has yet to be released for Dapper Drake, but others like the courier-authmysql, have they been integrated into the base metapackages or is the support for that module just not available?  I love the howto, it's very comprehensive and thorough, but it's frustrating to follow when you can't seem to find all the packages you need to get it to work.

I've considered going to an older version of Ubuntu, but 1) the server is based on the AMD-64 platform, and 2) Email is the last service I need to close this server config....I'd really hate to have to install all that stuff again!

Anyway, thanks for all the effort you've put into this HOWTO, it's one of the best I've seen for any service, much less 5 or 6 at the same time!

---

### Post by Alvadore on 2006-07-05
.

---

### Post by Eidar on 2006-07-06
Do anybody know a fix for the error message with Squirrelmail that says:

"**ERROR: Connection dropped by IMAP server.**"

---

### Post by Alvadore on 2006-07-06
Having problems after install.  Excerpt from mail.log follows.

[INDENT]Jul  6 05:55:55 mail postfix/trivial-rewrite[5518]: warning: mysql query failed: You have an error in your SQL syntax.  Check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
Jul  6 05:55:55 mail postfix/trivial-rewrite[5518]: fatal: mysql:/etc/postfix/mysql_domains.cf(0,100): table lookup problem
Jul  6 05:55:57 mail postfix/trivial-rewrite[5533]: warning: mysql query failed: You have an error in your SQL syntax.  Check the manual that corresponds to your MySQL server version for the right syntax to use near '' at line 1
Jul  6 05:55:57 mail postfix/trivial-rewrite[5533]: fatal: mysql:/etc/postfix/mysql_domains.cf(0,100): table lookup problem
[/INDENT]
Any ideas?
Or better yet, perhaps someone could post a copy of their WORKING config files?  That way we could just change the pertinant details and use them.

---

### Post by blind0wl on 2006-07-07
I spent a couple of days pulling my hair out and really need a clear explanation on adding users and how webmail mysql tables interact with whats been added for the base install.

Im confused with the webmail component and how it interacts with the sql tables the howto described creating.  And Im confused on how to actually create new users and how to authenticate them so they can login to the webmail client.  Im interested in roundcube as a webmail app, and I have actually got it working at one stage, but could never figure out how to add a user.

If anyone would be kind enough to put into simple terms how it all interacts with each other, it would be much appreciated.  The howto has been well done, but doesnt explain enough to the absolute n00b...such as myself.  Im hoping this hasnt been covered all ready and if it has I apologise, but any help would be appreciated.

Cheers

Dave

---

### Post by Alvadore on 2006-07-07
> **Alvadore said:**
> Having problems after install.  Excerpt from mail.log follows.



Okay, figured out that problem.  Error on my part editing .cfg files.  Corrected that, now the mail.log shows no errors (SWEET)!  However, user's cannot authenticate.  Checked logs, and usernames and passwords are correct.

Now, it all seems to work until I send a message to an account, then the log shows this.

Jul  7 17:24:12 mail postfix/smtpd[5278]: warning: connect #1 to subsystem private/rewrite: Connection refused

---

### Post by Alvadore on 2006-07-12
Okay, dumped the last install and started again from scratch on Breezy using version 4 of your install.  Everything went very well with one single exception.  I can send mail to it, it accepts the mail and write the maildir and delivers to it.  However, I cannot authenticate in Squirrelmail to check mail.  the mysql.log file has no errors, looks good.  The mail.log file shows these errors and I cannot find anything that would cause it, perhaps I'm overlooking something?  Here's the mail.log portion showing the error.

> Jul 12 05:19:46 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 12 05:19:46 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 12 05:19:46 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=al
Jul 12 05:19:46 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=w3asl3m3at
Jul 12 05:19:46 localhost imaplogin: authdaemon: starting client module
Jul 12 05:19:47 localhost imaplogin: authdaemon: REJECT
Jul 12 05:19:52 localhost imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Jul 12 05:19:52 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGOUT
Jul 12 05:19:52 localhost imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]

If anyone has a clue what the problem is please post a reply, email me, hell even a note around a rock would be welcome at this point....  PLEASE.

---

### Post by giorg on 2006-07-12
Can you authenticate through a simple telnet?

Andrea

---

### Post by giorg on 2006-07-12
Also, if you have a configuration with virtual domain, shouldn't use the **full** email address as username?

---

### Post by Alvadore on 2006-07-12
> **giorg said:**
> Can you authenticate through a simple telnet?

Andrea

I'm not sure how to achieve that (sorry, just left work and I'm a bit brain dead).  I ran the telnet test in the howto, it worked fine.

Al

---

### Post by Alvadore on 2006-07-12
> **giorg said:**
> Also, if you have a configuration with virtual domain, shouldn't use the **full** email address as username?

I tried that prior to finding your reply.  I was not able to log in, then I restarted MySQL and tried again with full email address as username.  I got in, saw two emails I'd sent to the mailbox and tried to send an email, it went out.  Then, when sending a second email the loging failure page came up.  Wierd!  Here's the log exerpt for that time frame (real addresses have been replaced)

> Jul 12 15:27:14 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 12 15:27:14 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 12 15:27:14 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=al@mydomainname.com
Jul 12 15:27:14 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=ch33s3
Jul 12 15:27:14 localhost imaplogin: authdaemon: starting client module
Jul 12 15:27:14 localhost imaplogin: authdaemon: ACCEPT, username [email]al@mydomainname.com[/email]
Jul 12 15:27:14 localhost imaplogin: LOGIN, user=al@mydomainname.com, ip=[::ffff:127.0.0.1], protocol=IMAP
Jul 12 15:27:15 localhost imaplogin: LOGOUT, user=al@mydomainname.com, ip=[::ffff:127.0.0.1], headers=0, body=870, time=1
Jul 12 15:27:37 localhost postfix/smtpd[7461]: connect from localhost.localdomain[127.0.0.1]
Jul 12 15:27:37 localhost postfix/smtpd[7461]: 8248ABF28: client=localhost.localdomain[127.0.0.1]
Jul 12 15:27:37 localhost postfix/cleanup[7466]: 8248ABF28: message-id=<1100.192.168.1.199.1152732457.squirrel@webmail.mydomainname.com>
Jul 12 15:27:37 localhost postfix/smtpd[7461]: disconnect from localhost.localdomain[127.0.0.1]
Jul 12 15:27:37 localhost postfix/smtp[7471]: connect to 127.0.0.1[127.0.0.1]: Connection refused (port 10024)
Jul 12 15:27:38 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 12 15:27:38 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 12 15:27:38 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=al@mydomainname.com
Jul 12 15:27:38 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=ch33s3
Jul 12 15:27:38 localhost imaplogin: authdaemon: starting client module
Jul 12 15:27:40 localhost imaplogin: authdaemon: REJECT
Jul 12 15:27:40 localhost postfix/smtp[7471]: 8248ABF28: to=<user@somedomain.com>, relay=none, delay=3, status=deferred (connect to 127.0.0.1[127.0.0.1]: Connection refused)
Jul 12 15:27:45 localhost imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]
Jul 12 15:27:45 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGOUT
Jul 12 15:27:45 localhost imaplogin: LOGOUT, ip=[::ffff:127.0.0.1]
Jul 12 15:27:59 localhost imaplogin: Connection, ip=[::ffff:127.0.0.1]
Jul 12 15:27:59 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN
Jul 12 15:27:59 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=al@mydomainname.com
Jul 12 15:27:59 localhost imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=ch33s3
Jul 12 15:27:59 localhost imaplogin: authdaemon: starting client module
Jul 12 15:27:59 localhost imaplogin: authdaemon: REJECT
Jul 12 15:28:04 localhost imaplogin: LOGIN FAILED, ip=[::ffff:127.0.0.1]

---

### Post by giorg on 2006-07-13
> **Alvadore said:**
> I tried that prior to finding your reply.  I was not able to log in, then I restarted MySQL and tried again with full email address as username.  I got in, saw two emails I'd sent to the mailbox and tried to send an email, it went out.  Then, when sending a second email the loging failure page came up.  Wierd!  Here's the log exerpt for that time frame (real addresses have been replaced)

I would say definitely you should log in with full email address. The second error means that the daemon is not running, maybe is crashed for some reason... you should first check with ps, then telnet localhost 110 at the prompt user (username) then the password and see if it is accepted...

---

### Post by Alvadore on 2006-07-13
> **giorg said:**
> The second error means that the daemon is not running
Which daemon are you referring to?

---

### Post by giorg on 2006-07-13
> **Alvadore said:**
> Which daemon are you referring to?

This error is saying: "I cannot send the email because I could not connect to the daemon". So the daemon should be posftix: check it out with ps. But sometimes these errors are a little confusing, so at your place I would check also courier. You should have opened the ports 25, 110 and 143 on localhost.

Andrea

---

### Post by Alvadore on 2006-07-13
> **giorg said:**
> I would check also courier. You should have opened the ports 25, 110 and 143 on localhost.
Andrea

It's fixed...  Yaaay!  After enabling debugging inauthdaemonrc I found that it authmysqlrc was trying to use encrypted passwords.  Disabled it and all is well.  As a matter of fact, after it tested well on the temporary server, I set it up on my live server.  I even managed to find a forwarding plugin which was easily configured for this setup.  I'm attaching a zip file of it in case anyone wants to easily allow users to forward.  They can enable forwarding in Squirrelmail.  All that you need to do is this:
[LIST=1]mkdir /usr/share/squirrelmail/plugins/mail_fwd[/LIST]
[LIST=2]unzip mail_fwd.zip into the folder above[/LIST]
[LIST=3]Edit config.php and change line 26 ($mysql_manager_pwd = '';) to the password for your MySQL user "mail"[/LIST]
[LIST=4]Run Squirrelmail config (/var/www/squirrelmail/config/conf.pl)[/LIST]
[LIST=5]Select option 8 (plugins)[/LIST]
[LIST=6]Select option for plugin "mail_fwd"[/LIST]
[LIST=7]Save config and exit[/LIST]


To set up forwarding from Squirrelmail:
[LIST=1]Log into Squirrelmail[/LIST]
[LIST=2]click on "options"[/LIST]
[LIST=3]click on "Mail Forwarding Options"[/LIST]
[LIST=4]The rest is obvious[/LIST]

---

### Post by Alvadore on 2006-07-17
Spamassassin question

I've managed to get a system set up correctly and after viewing the mail log I decided to do the bayes training you noted in the howto.

I'm a bit fonfused about something.  In the howto you listed two commands to run to train bayes.  The first is this:
sa-learn --showdots -C /etc/spamassassin --spam /var/spool/mail/virtual/quarantine/.spam/*

What is confusing me is that the command points to a maildir that is not there.  I scanned through the howto very carefully and found no other reference to this directory.  Is Spamassassin even set up correctly?  If so, will it create this Maildir automatically?  Was there something I should have done that was not llisted?  Also, lots of SPAM is showing up in the root@localhost account.  Perhaps further tweakin gis in order? Any thoughts on this would be very helpful.

---

### Post by veselu on 2006-07-20
Hello everyone.

First let me thank flurdy for this great tutorial.

I followed the instuctions by book but i'm stuck at the Test point, to be more precise here:

```
#telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mail.server.com ESMTP Postfix (Ubuntu)
EHLO mail.server.com
250-mail.server.com
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250-AUTH=LOGIN PLAIN DIGEST-MD5 CRAM-MD5
250 8BITMIME
MAIL FROM: veselu@gmail.com
250 Ok
RCPT TO: postmaster@localhost
451 Server configuration error
```

This is the error given in mail.log for postfix:

```
NOQUEUE: reject: RCPT from localhost[127.0.0.1]: 451 Server configuration error; from=<veselu@gmail.com> to=<postmaster@localhost> proto=ESMTP helo=<mail.server.com>
451 Server configuration error
Jul 20 12:45:45 server postfix/smtpd[16070]: timeout after RCPT from localhost[127.0.0.1]
```

What is the matter?

---

### Post by Alvadore on 2006-07-25
[COLOR="Red"]**Spamassassin question Part Duex**[/COLOR]:

System is up and running, using it daily for several users.
I've been digging around trying to figure out why Spamassassin is not working.

I edited [COLOR="Green"]/etc/spamassassin/local.cf[/COLOR] which now reads as follows:

> required_score           5.0
rewrite_header Subject *****SPAM*****
skip_rbl_checks         0
use_razor2              0
use_dcc                 0
use_pyzor               0
use_bayes               1
bayes_path              /etc/spamassassin/bayes
bayes_file_mode         0770

The results are that SPAM is STILL delivered to root@localhost, nothing deliveres to /virtual/quarantine, SPAM gets through to users and has no header subject "*****SPAM*****".

To me, this looks like Spamassassin is not working correctly.
Is anyone else having any luck (good or bad) with Spamassassin in this configuration?
Any and all help would be appreciated.

---

### Post by Mazak on 2006-07-27
Download DB Package from [http://pear.php.net/package/DB](http://pear.php.net/package/DB)

Unzip it ... then move DB.php and DB folder into /usr/share/php

Hope this helps


> **cconk01 said:**
> I think i have gotten pretty far setting up the email, but i went to the test page and i have recieved this error message: 

> 
ERROR: Required PHP PEAR DB support is not available. Is PEAR installed and is the include path set correctly to find DB.php? The include path is now: ".:/usr/share/php:/usr/share/pear".


then when i try to log in with my root username i get these error messages
[quote]
Warning: include_once(DB.php) [function.include-once]: failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: include_once() [function.include]: Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /usr/share/squirrelmail/functions/db_prefs.php on line 40
ERROR:
Could not include PEAR database functions required for the database backend.
Is PEAR installed, and is the include path set correctly to find DB.php?
Please contact your system administrator and report this error.


What have i done wrong?[/QUOTE]

---

### Post by Truster on 2006-09-13
Hi.

I have set up an email server as descripted in the howto on Ubuntu server 6.0.6. Everything seems to be work fine, i can login via terminal, but when i try to login with squirrelmail, i always geht the folowing error: at the top: ERROR: Could not complete request.
Query: SELECT "INBOX"
Reason Given: Unable to open this mailbox.

At left side: ERROR: Connection dropped by IMAP server.
Query: SUBSCRIBE "INBOX.Sent"

Firefox says also "unable to open this mailbox."

no more Infos at syslog, maillog

---

### Post by Truster on 2006-09-13
Hi again.

ok the last error is because, i havn't any mails in my box yet, so i tried to send some to myself nut postfix shows this error:
recipient [email]truster (at) chatfreak dot at[/email]: gid not found in virtual_gid_maps

the user and the alias is in the database, the mysql_gid.cf file is correct. What's wrong?

---

### Post by giorg on 2006-09-14
Hi,

it looks like you don't have the gid correcty configured. Can you post your main.cf? Did you take a look to the mysql logs?

---

### Post by Truster on 2006-09-14
i hate typos :D

Found one in the main.cf, now the mailserver is working correctly.

Damn, i wish, there mor howtos like this one: easy to read and understand and well explained ;)

Great work!

---

### Post by Truster on 2006-09-15
Suggestions about TLS/SSL:

i suggest to create a CA Certificate with the CA.pl script
e.g
```
/usr/lib/ssl/misc/CA.pl -newca
```
hit RETURN

Enter the required information

Example:
```
Making CA certificate ...
Generating a 1024 bit RSA private key
.................................++++++
...............++++++
writing new private key to './demoCA/private/cakey.pem'
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:AT
State or Province Name (full name) [Some-State]:AUSTRIA
Locality Name (eg, city) []:MYCITY
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Rast + Ruh GmbH
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:Mailserver Root Certificate Authority
Email Address []:webmaster@mailserver.abc

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for ./demoCA/private/cakey.pem:
Check that the request matches the signature
Signature ok
Certificate Details:
        Serial Number:
            ab:c2:1e:02:cb:e0:eb:71
        Validity
            Not Before: Sep 15 12:16:49 2006 GMT
            Not After : Sep 12 12:16:49 2016 GMT
        Subject:
            countryName               = AT
            stateOrProvinceName       = AUSTRIA
            organizationName          = Rast + Ruh GmbH
            commonName                = Mailserver Root Certificate Authority
            emailAddress              = webmaster@mailserver.abc
        X509v3 extensions:
            X509v3 Basic Constraints: 
                CA:FALSE
            Netscape Comment: 
                OpenSSL Generated Certificate
            X509v3 Subject Key Identifier: 
                DF:33:B9:82:B0:26:3A:99:4C:B9:41:C3:09:45:CA:79:7D:4B:67:85
            X509v3 Authority Key Identifier: 
                keyid:DF:33:B9:82:B0:26:3A:99:4C:B9:41:C3:09:45:CA:79:7D:4B:67:85

Certificate is to be certified until Sep 12 12:16:49 2016 GMT (3650 days)

Write out database with 1 new entries
Data Base Updated

```

You have to remember the choosen phassphrase. you will need it later to sign the certificate

Now let's create the private key with:
```
/usr/lib/ssl/misc/CA.pl -newreq-nodes
```

Fill out the required field as you have it done before.
REMEMBER: The common name (CN) must be the server adress eg sv00.mydomain.at

```
Generating a 1024 bit RSA private key
.................++++++
.........++++++
writing new private key to 'newkey.pem'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:AT
State or Province Name (full name) [Some-State]:AUSTRIA
Locality Name (eg, city) []:MYCITY
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Rast + Ruh GMBH
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:sv00.mydomain.at
Email Address []:

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:
Request is in newreq.pem, private key is in newkey.pem

```

So we have the required certificate to self-sign our one with:
```
/usr/lib/ssl/misc/CA.pl -sign
```

This will self-sign our certificate with our own CA-Certificate

```
Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for ./ChatfreakCA/private/cakey.pem:
Check that the request matches the signature
Signature ok
Certificate Details:
        Serial Number:
            ab:c2:1e:02:cb:e0:eb:72
        Validity
            Not Before: Sep 15 12:22:25 2006 GMT
            Not After : Sep 12 12:22:25 2016 GMT
        Subject:
            countryName               = AT
            stateOrProvinceName       = AUSTRIA
            localityName              = MYCITY
            organizationName          = Rast + Ruh GMBH
            commonName                = sv00.mydomain.at
        X509v3 extensions:
            X509v3 Basic Constraints: 
                CA:FALSE
            Netscape Comment: 
                OpenSSL Generated Certificate
            X509v3 Subject Key Identifier: 
                22:AA:9C:E1:9E:3C:B3:B4:A4:6C:7C:1E:76:54:D0:20:33:7C:0C:FA
            X509v3 Authority Key Identifier: 
                keyid:12:E2:B5:E0:E2:69:E3:F8:10:1D:82:F5:9D:B7:AE:3B:11:E2:FA:14

Certificate is to be certified until Sep 12 12:22:25 2016 GMT (3650 days)
Sign the certificate? [y/n]:y


1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated
Signed certificate is in newcert.pem

```

now type ls and see, wat we have, it should look like this
```
demoCA  newcert.pem  newkey.pem  newreq.pem
```
You can copy newcert.pem and newkey.pem to your /etc/postfix directory and update the main.cf file

To use the certificate with courier, both (key and certificate) file must be in one file. You can do this with:
```
root@test:~# cat newkey.pem >> imapd.pem
root@test:~# cat newcert.pem >> imapd.pem
```

and copy the new file to /etc/courier/

now cd to demoCA

you'll find a file named cacert.pem

you can use this file to import it in Internet Explorer/Outlook/Entourage/

This will result in no nag of wrong root Certificate :)

Hint: you can edit the /usr/lib/ssl/misc/CA.pl and /usr/lib/ssl/openssl.cnf to adjust paths, date, and other settings

---

### Post by 3dmonkey3000 on 2006-09-23
I am running a Ubuntu 6.06 LTS Server, with Postfix as MTA, and Courier-imap as my IMAP server. I also have squirrelmail as my webmail interface.

When ever i login to Squirrel Mail, I get this error:
=========================================================
ERROR: Connection dropped by IMAP server.
=========================================================
Has anyone got any ideas, Because all the above posts are all scrambled around all over the place, and are hard to follow.

Any one??

-3d

---

### Post by mdelves on 2006-09-26
I have setup a Postfix/Mysql/Vhost/... configuration though I am wanting to implement procmail for the purpose of having server side mail filtering. Does anyone know of how this would be intergrated? I am not too sure if simply having procmail run is the best solution or if there are other ways.

--EDIT--
Sorry folks, stupid question to which I just found the answer. Should have read the howto in more detail
--EDIT--

--EDIT--
It seems like there is some functionality there to extend upon everything, though not completed just yet. I will do some more looking around to figure out just how to use procmail to get the required procmailrc file from the MySQL database. If anyone knows of how to do this, please let me know.
--EDIT--

Thanks,
Matthew Delves

---

### Post by shakyamuni on 2006-10-19
I've been trying to solve this issue, but i cannot find the problem. this is the error message when I try to log in to squirrelmail:
ERROR: Connection dropped by IMAP server.

Any ideas?

thanks in advance,

Carlos.

---

### Post by shakyamuni on 2006-10-19
I solved the problem of above, but now i have this error:
"ERROR: Could not complete request.
Query: CREATE "INBOX.Sent" Reason Given: Cannot create this folder."

Does anyone know what's the problem now?

thank you.

regards,
Carlos.

---

### Post by shakyamuni on 2006-10-24
Is there anybody looking at this forum?

regards,

Carlos.

---

### Post by constantinarol on 2006-10-25
Yeah .. me .. I am looking at it.. but is 11 pages long... dunno where to start from..

---

### Post by willg on 2006-10-25
Sorry to repost this, it looks like this forum is a little more active than the other How To. 

I was able to get most everything running after several attempts. However, two problems still remain

1. I have seen this post twice, but not seen a solution. Basically, mail is getting delivered to /var/spool/mail/virtual/willg/ but is not showing up in Squirrelmail (when it was working)..which brings me to my next problem

2. I have also seen this post, the solution was to download DB.php and place it in /usr/share/php. On my machine this file and the DB directory already exist in /usr/share/php, so it would seem that is not the issue. After following the Squirrelmail section about adding mysql://usernameassword@127.0.0.1/database in the DSN for Address Book section and DSN for Preferences section I now get the following error when I try to login to Squirrelmail


Warning: main(DB.php): failed to open stream: No such file or directory in /usr/share/squirrelmail/functions/db_prefs.php on line 40

Warning: main(): Failed opening 'DB.php' for inclusion (include_path='.:/usr/share/pear') in /usr/share/squirrelmail/functions/db_prefs.php on line 40
ERROR:
Could not include PEAR database functions required for the database backend.
Is PEAR installed, and is the include path set correctly to find DB.php?
Please contact your system administrator and report this error.

Any help would be greatly appreciated. Thanks!

---

### Post by elguapo on 2006-12-13
I had the same problem with PEAR, but managed to fix it bij checking where PEAR is installed (locate pear) and then add the correct path to php.ini.

Now I have another problem: when trying to login in courier-imap throught telnet I recieve the following error:
> * BYE [ALERT] Fatal error: Maildir: No such file or directory
Connection closed by foreign host.Not good...

Any fix will do, since I will be the only one using the machine, I don't mind if its quick 'n dirty.

---

### Post by SeaStorm on 2006-12-22
Have the same Problem!

when I try to login, mail.log says 

```
Dec 22 12:26:22 systonia imaplogin: Connection, ip=[::ffff:127.0.0.1]

Dec 22 12:26:22 systonia imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], command=LOGIN

Dec 22 12:26:22 systonia imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], username=sea@localhost

Dec 22 12:26:22 systonia imaplogin: LOGIN: DEBUG: ip=[::ffff:127.0.0.1], password=test

Dec 22 12:26:22 systonia imaplogin: authdaemon: starting client module

Dec 22 12:26:22 systonia imaplogin: authdaemon: ACCEPT, username sea@localhost

Dec 22 12:26:22 systonia imaplogin: chdir Maildir: No such file or directory
```

/var/spool/mail/virtual/sea/ exists. owner is virtual. chmod 777. in the DB the vars are:

home=/var/spool/mail/virtual
maildir=sea/




When I send a email to the account, mail.log sais:

Dec 22 12:17:42 systonia postfix/qmgr[32666]: AA2E96003D2: from=<root@localhost>, size=2017, nrcpt=1 (queue active)
Dec 22 12:17:42 systonia postfix/virtual[17089]: AA2E96003D2: to=<sea@localhost>, relay=virtual, delay=15408, status=deferred (recipient sea@localhost: bad gid sea@localhost in virtual_gid_maps)


dont know why this appears :\


But I can send Emails ;D


Super HowTo anyway ! Thanks for that great work!

---

### Post by cheer on 2007-01-22
complete step by step guide to install, configure and run these packages:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail+Postgrey

Any one can e-mail this page because I can't access it during half way configuring mail mail server. I think it is a routing problem from my country to flurdy.com website.

please e-mail to [email]kypang@d-xpert.com[/email]

it is urgert.

thanks

regards,
cheer

---

### Post by jake3988 on 2007-01-22
Ugh.  Like most How-Tos it assumes you are a complete expert and explains nothing.

Its a great starting point and a lot of work was surely placed into it, but please, actually explain things.  "Add this and don't why or what it does' doesn't help. Sorry.

---

### Post by godlike on 2007-02-16
LOL i hear your frustration at the ubuntu howtos for mail servers. I tried MANY of them but I guess Im too computer stupid becuase not one worked for me. I ended up just firing up another seperate box and using suse with qmail was way easier lol

---

### Post by cybernet on 2008-03-05
mirror for flurdy.com/docs/postfix/


[http://www.scribd.com/doc/2218859/How-to-set-up-a-mail-server-on-a-GNU-Linux-system](http://www.scribd.com/doc/2218859/How-to-set-up-a-mail-server-on-a-GNU-Linux-system)

---

### Post by fade2gray on 2008-06-23
> **cybernet said:**
> mirror for flurdy.com/docs/postfix/


[http://www.scribd.com/doc/2218859/How-to-set-up-a-mail-server-on-a-GNU-Linux-system](http://www.scribd.com/doc/2218859/How-to-set-up-a-mail-server-on-a-GNU-Linux-system)

Hey cybernet, any possibility of you updating your mirror to reflect flurdy's 7th edition guide? :-k

Also, would anyone know if firestarter could be used, instead of shorewall, when using this guide?

Thanks.

---

### Post by DataMatrix on 2009-01-18
> **fade2gray said:**
> 
Also, would anyone know if firestarter could be used, instead of shorewall, when using this guide?

Thanks.
I'm using firestarter on several server machines, you just need to set up the allowed ports, eg 110 for pop3, 25 for smtp and so on.

My problem is that I constantly get Recipient address rejected when i try to e-mail myself from my google e-mail (or just about anywhere). :confused:

---

### Post by zim2dive on 2009-05-28
Tried following this under Jaunty.. I get```
>aptitude install libsasl2-modules-sql libgsasl7 libauthen-sasl-cyrus-perl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by flurdy on 2009-05-29
FYI.
The longer and more detailed thread got moved yesterday for some reason.??

But you can find it here: [http://ubuntuforums.org/showthread.php?t=185913](http://ubuntuforums.org/showthread.php?t=185913)

---

### Post by zim2dive on 2009-05-29
FWIW, I just tried installing an impad yesterday using the guide, and then on my own... I was trying to use RoundCube as web access to it.

- courier-imapd could not find my $USER/Mail folders when I installed all as root (which the courier page says not to).. when I did not install all as root I got the error listed 2 posts above.
- uw-imapd did not allow plaintext logins.. I think it can be rebuilt, but life is too short when...
- dovecot installed and worked with no tweaking needed

so for now, I guess I'm going to use dovecot.

my needs are only:
- imapd
- spamassassin
- mta

I'm totally indifferent to what I use, only that it works.

---

### Post by candoyo on 2010-04-24
Hi Flurdy and everyone else!

Thanks a lot of writing this amazing guide. I really appreciate, it will make my life a lot easier 

I have installed the AMI image into my AWS account. I have installed flurdy-amis/ubuntu-mail-server-webmail.
I can access phpmyadmin via the internet. But, I am not sure what's the user name and password for phpmyadmin? I also logged into the server via ssh but was not able to run mysqladmin command. It said I didn't have enough privileges to access mysqladmin. But I am logged in as root... why cant I use mysqladmin?

Any help wold be highly appreciated. Thanks again for the great work 

-Shaq

---

### Post by mtk- on 2011-03-12
Hi,

i follow tutorial "complete step by step guide to install:
Ubuntu + Postfix + Courier IMAP + MySQL + Amavisd-new + SpamAssassin + ClamAV + SASL + TLS + SquirrelMail+Postgrey" and setup mail server with virtual users. 

How i can change user password with squirrelmail ?

---

### Post by duceduc on 2011-03-12
I believe there is password add-on module in squirrelmail that needs to be install to be able to change password within squirrelmail client.

---

### Post by mtk- on 2011-03-12
> **duceduc said:**
> I believe there is password add-on module in squirrelmail that needs to be install to be able to change password within squirrelmail client.

Thanks. I find plugin "change_sqlpass" but i can't get it to work. I Think my configs are wrong. Can somebody look at this config and tell whats wrong.

I try to change password and got error: DATABASE ERROR: could not lookup old password:

```

<?php

/**
  * SquirrelMail Change SQL Password Plugin
  * Copyright (C) 2001-2002 Tyler Akins
  *               2002 Thijs Kinkhorst <kink@users.sourceforge.net>
  *               2002-2005 Paul Lesneiwski <paul@openguild.net>
  * This program is licensed under GPL. See COPYING for details
  *
  * @package plugins
  * @subpackage Change SQL Password
  *
  */


   // Global Variables, don't touch these unless you want to break the plugin
   //
   global $csp_dsn, $password_update_queries, $lookup_password_query,
          $force_change_password_check_query, $password_encryption,
          $csp_salt_query, $csp_salt_static, $csp_secure_port,
          $csp_non_standard_http_port, $csp_delimiter, $csp_debug,
          $min_password_length, $max_password_length, $include_digit_in_password,
          $include_uppercase_letter_in_password, $include_lowercase_letter_in_password,
          $include_nonalphanumeric_in_password;



   // csp_dsn
   //
   // Theoretically, any SQL database supported by Pear should be supported
   // here.  The DSN (data source name) must contain the information needed
   // to connect to your database backend. A MySQL example is included below.
   // For more details about DSN syntax and list of supported database types,
   // please see:
   //   http://pear.php.net/manual/en/package.database.db.intro-dsn.php
   //
   $csp_dsn = 'mysql://user:password@localhost/maildb';



   // lookup_password_query
   //
   // This plugin will always verify the user's old password
   // against their login password, but an extra check can also
   // be done against the database for more security if you
   // desire.  If you do not need the extra password check,
   // make sure this setting is empty.
   //
   // This is a query that returns a positive value if a user
   // and password pair are found in the database.
   //
   // This query should return one value (one row, one column), the
   // value being ideally a one or a zero, simply indicating that 
   // the user/password pair does in fact exist in the database.
   //
   //   %1 in this query will be replaced with the full username
   //      (including domain), such as "jose@example.com"
   //   %2 in this query will be replaced with the username (without
   //      any domain portion), such as "jose"
   //   %3 in this query will be replaced with the domain name,
   //      such as "example.com"
   //   %4 in this query will be replaced with the current (old)
   //      password in whatever encryption format is needed per other
   //      plugin configuration settings (Note that the syntax of
   //      the password will be provided depending on your encryption
   //      choices, so you NEVER need to provide quotes around this
   //      value in the query here.)
   //   %5 in this query will be replaced with the current (old)
   //      password in unencrypted plain text.  If you do not use any
   //      password encryption, %4 and %5 will be the same values,
   //      except %4 will have double quotes around it and %5 will not.
   //
   //$lookup_password_query = '';
   // TERRIBLE SECURITY: $lookup_password_query = 'SELECT count(*) FROM users WHERE username = "%1" AND plain_password = "%5"';
   $lookup_password_query = 'SELECT count(*) FROM users WHERE username = "%1" AND crypt_password = %4';



   // password_update_queries
   //
   // An array of SQL queries that will all be executed 
   // whenever a password change attempt is made.
   //
   // Any number of queries may be included here.
   // The queries will be executed in the order given here.
   //
   //   %1 in all queries will be replaced with the full username
   //      (including domain), such as "jose@example.com" 
   //   %2 in all queries will be replaced with the username (without 
   //      any domain portion), such as "jose"
   //   %3 in all queries will be replaced with the domain name, 
   //      such as "example.com"
   //   %4 in all queries will be replaced with the new password
   //      in whatever encryption format is needed per other
   //      plugin configuration settings (Note that the syntax of 
   //      the password will be provided depending on your 
   //      encryption choices, so you NEVER need to provide quotes 
   //      around this value in the queries here.)
   //   %5 in all queries will be replaced with the new password
   //      in unencrypted plain text - BEWARE!  If you do not use
   //      any password encryption, %4 and %5 will be the same 
   //      values, except %4 will have double quotes around it
   //      and %5 will not.
   //
   $password_update_queries = array(
            'UPDATE users SET crypt_password = %4 WHERE username = "%1"',
//            'UPDATE user_flags SET force_change_pwd = 0 WHERE username = "%1"',
//            'UPDATE users SET crypt_password = %4, force_change_pwd = 0 WHERE username = "%1"',
                                   );



   // force_change_password_check_query
   //
   // A query that checks for a flag that indicates if a user
   // should be forced to change their password.  This query
   // should return one value (one row, one column) which is
   // zero if the user does NOT need to change their password, 
   // or one if the user should be forced to change it now. 
   //
   // This setting should be an empty string if you do not wish
   // to enable this functionality.
   //
   //   %1 in this query will be replaced with the full username
   //      (including domain), such as "jose@example.com" 
   //   %2 in this query will be replaced with the username (without 
   //      any domain portion), such as "jose"
   //   %3 in this query will be replaced with the domain name, 
   //      such as "example.com"
   //
   //$force_change_password_check_query = 'SELECT IF(force_change_pwd = "yes", 1, 0) FROM users WHERE username = "%1"';
   //$force_change_password_check_query = 'SELECT force_change_pwd FROM users WHERE username = "%1"';
   $force_change_password_check_query = '';



   // password_encryption
   //
   // What encryption method do you use to store passwords
   // in your database?  Please use one of the following,
   // exactly as you see it:
   //
   //   NONE          Passwords are stored as plain text only
   //   MYSQLPWD      Passwords are stored using the MySQL password() function
   //   MYSQLENCRYPT  Passwords are stored using the MySQL encrypt() function 
   //   PHPCRYPT      Passwords are stored using the PHP crypt() function 
   //   MD5CRYPT      Passwords are stored using encrypted MD5 algorithm
   //   MD5           Passwords are stored as MD5 hash
   //
   $password_encryption = 'MYSQLENCRYPT';



   // csp_salt_query
   // csp_salt_static
   //
   // Encryption types that need a salt need to know where to get
   // that salt.  If you have a constant, known salt value, you
   // should define it in $csp_salt_static.  Otherwise, leave that
   // value empty and define a value for the $csp_salt_query.
   //
   // Leave both values empty if you do not need (or use) salts
   // to encrypt your passwords.
   //
   // The query should return one value (one row, one column) which 
   // is the salt value for the current user's password.  This
   // query is ignored if $csp_salt_static is anything but empty.
   //
   //   %1 in this query will be replaced with the full username
   //      (including domain), such as "jose@example.com"
   //   %2 in this query will be replaced with the username (without
   //      any domain portion), such as "jose"
   //   %3 in this query will be replaced with the domain name,
   //      such as "example.com"
   //
   //$csp_salt_static = 'LEFT(crypt_password, 2)';
   //$csp_salt_static = '"a4"';  // use this format with MYSQLENCRYPT
   //$csp_salt_static = '$2$blowsomefish$';  // use this format with PHPCRYPT
   //$csp_salt_static = '';
   $csp_salt_static = 'LEFT(password, 2)';

   //$csp_salt_query = 'SELECT SUBSTRING_INDEX(crypt_password, '$', 1) FROM users WHERE username = "%1"';
   //$csp_salt_query = 'SELECT SUBSTRING(crypt_password, (LENGTH(SUBSTRING_INDEX(crypt_password, '$', 2)) + 2)) FROM users WHERE username = "%1"';
   $csp_salt_query = 'SELECT salt FROM users WHERE username = "%1"';
   //$csp_salt_query = '';



   // csp_secure_port
   // 
   // You may ensure that SSL encryption is used during password 
   // change by setting this to the port that your HTTPS is served
   // on (443 is typical).  Set to zero if you do not wish to force
   // an HTTPS connection when users are changing their passwords.
   //
   // You may override this value for certain domains, users, or
   // service levels through the Virtual Host Login (vlogin) plugin 
   // by setting a value(s) for $vlogin_csp_secure_port in the vlogin
   // configuration.
   //
   $csp_secure_port = 0;
   //$csp_secure_port = 443;



   // csp_non_standard_http_port
   //
   // If you serve standard HTTP web requests on a non-standard
   // port (anything other than port 80), you should specify that
   // port number here.  Set to zero otherwise.
   //
   // You may override this value for certain domains, users, or
   // service levels through the Virtual Host Login (vlogin) plugin 
   // by setting a value(s) for $vlogin_csp_non_standard_http_port 
   // in the vlogin configuration.
   //
   //$csp_non_standard_http_port = 8080;
   $csp_non_standard_http_port = 0;



   // min_password_length
   // max_password_length
   // include_digit_in_password
   // include_uppercase_letter_in_password
   // include_lowercase_letter_in_password
   // include_nonalphanumeric_in_password
   //
   // You can set the minimum and maximum password lengths that
   // you accept or leave those settings as zero to indicate that
   // no limit should be applied.
   //
   // Turn on any of the other settings here to check that the
   // new password contains at least one digit, upper case letter,
   // lower case letter and/or one non-alphanumeric character.
   //
   $min_password_length = 6;
   $max_password_length = 0;
   $include_digit_in_password = 0;
   $include_uppercase_letter_in_password = 0;
   $include_lowercase_letter_in_password = 0;
   $include_nonalphanumeric_in_password = 0;



   // csp_delimiter
   //
   // if your system has usernames with something other than
   // an "@" sign separating the user and domain portion,
   // specify that character here
   //
   //$csp_delimiter = '|';
   $csp_delimiter = '@';
   


   // debug mode
   //
   $csp_debug = 0;



?>

```

---

### Post by chrinabuntu on 2011-03-12
I know this is off-topic, but it just happened to catch my eye that you are in Japan, duceduc. The footage coming from Japan is just devastating. I hope all the people in your world are ok!!! (You are posting here, so that's great!) So sad to see those images on the news!

Chris in the Q

---

### Post by duceduc on 2011-03-12
chrinabuntu:

Thanks for your concern. Japan suffered heavy damage mainly around the epic center. I am not too close from it but we did felt it heavy. We are not out of the woods yet. The many aftershocks we are having currently are expected to last for a month. Some were as high as 7M.

---

