---
title: "HowTo Install Request-Tracker 3.4 on Ubuntu Breezy 5.10"
date: 2006-05-11
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-05-11
**HowTo Install Request-Tracker 3.4 on Ubuntu Breezy 5.10**
This HowTo is Originally posted at:
[http://howtoforums.net/viewtopic.php?t=23](http://howtoforums.net/viewtopic.php?t=23)

"RT is an enterprise-grade ticketing system which enables a group of people to intelligently and efficiently manage tasks, issues, and requests submitted by a community of users."
-- [http://bestpractical.com/rt/](http://bestpractical.com/rt/)

This HowTo will explain how to install request-tracker on a clean Ubuntu Server install.
It is tested on Ubuntu Breezy 5.10 and mite work with slight modifications on other versions or Debian based distros.
I create a root user as apposed to using sudo, just because i am used to it but you may add sudo in front of the commands if you prefer the sudo security default method of Ubuntu.

To activate the root user:
```

sudo passwd root

```

Enable universe in your Sources.list
```

cp -vpr /etc/apt/sources.list /etc/apt/sources.list.orig
vim /etc/apt/sources.list
#comment this:
###deb cdrom:...
apt-get update
apt-get install postgresql libcgi-fast-perl apache2-mpm-prefork libapache2-mod-fcgid lynx apache2-doc libapache2-mod-perl2
apt-get install request-tracker3.4

```


# BKUP the RT config file...I like to do this for every conf file I modify
```

cp -vpr /etc/request-tracker3.4/RT_SiteConfig.pm /etc/request-tracker3.4/RT_SiteConfig.pm.orig

```

```

vim /etc/request-tracker3.4/RT_SiteConfig.pm

```

Customize and add this...
```

Set($DatabaseHost   , 'localhost');
Set($DatabaseRTHost , 'localhost');

```

Create the user for the RT database
```

su postgres
psql -d template1
CREATE USER rtuser WITH PASSWORD 'wibble' CREATEDB NOCREATEUSER;
\q
exit

```


Customize Postgresql permissions
```

vim /etc/postgresql/7.4/main/pg_hba.conf
at the bottom of the file along with the other similar lines - but
above existing entries.
###according to install.debian for request-tracker
host    template1   rtuser    127.0.0.1    255.255.255.255   password
local   template1   rtuser                                   password
host    rtdb        rtuser    127.0.0.1    255.255.255.255   password
local   rtdb        rtuser                                   password

```
```

vim /etc/postgresql/7.4/main/postgresql.conf
make sure this is enabled
tcpip_socket = true

```

Restart Database
```

/etc/init.d/postgresql-7.4 restart

```


Test db connection
```

psql -d template1 -U rtuser -W
#enter password at the prompt

```

Create the RT DataBase
```

/usr/sbin/rt-setup-database-3.4 --action init --dba rtuser --prompt-for-dba-password

```


Configure Apache2
```

vim /etc/apache2/sites-available/default

```
Add the following line to the VirtualHost section of Apache from which you wish to serve RT
```

    Include "/etc/request-tracker3.4/apache2-modperl2.conf"

```
```

vim /etc/request-tracker3.4/apache2-modperl2.conf
comment this
#PerlFreshRestart Off

```

Fix for the error complaining about can't find stuff
```

ln -s /usr/lib/perl5/Bundle/Apache2.pm /usr/lib/perl5/Apache2.pm
ln -s /usr/lib/perl5/Apache2/compat.pm /usr/lib/perl5/Apache/compat.pm
ln -s /usr/lib/perl5/Apache2/RequestUtil.pm /usr/lib/perl5/Apache/RequestUtil.pm

```

Restart Apache
```

/etc/init.d/apache2 force-reload

```


### You can now login to [http://yourdomain.com/rt](http://yourdomain.com/rt)
using user root and password "password" (without quotation marks of course)
change this passwd asap via the Configuration menu


######## Mail Settings ########
This part is really network specific, but if you are going to use Request-Tracker as "support" mailbox organizer so to speak, than you need to set up the system to pull email.
One method would be using fetchmail which can grab mail from an IMAP/POP3 account and put it in the system.
The links below describe this process:
 [http://wiki.bestpractical.com/index.cgi?POP3Mailgate](http://wiki.bestpractical.com/index.cgi?POP3Mailgate)
 [http://wiki.bestpractical.com/index.cgi?ManualInstallation](http://wiki.bestpractical.com/index.cgi?ManualInstallation) (Search for "Setting Up the Mail Gateway") for the basic email settings

These are the packages if your going for the configuration with fetchmail and postfix as the outgoing smtp server
```

apt-get install fetchmail fetchmailconf  fetchmail-ssl postfix ca-certificates

```

##DON'T Forget:
you need to have "CreateTicket" permissions on "Queue General" or any queue that you throw the emails in from the user fetching the mail

Enjoy!

---

