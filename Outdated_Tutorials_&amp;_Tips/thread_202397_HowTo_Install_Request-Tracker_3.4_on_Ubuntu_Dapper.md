---
title: "HowTo Install Request-Tracker 3.4 on Ubuntu Dapper 6.06"
date: 2006-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-06-23
**_HowTo Install Request-Tracker 3.4 on Ubuntu Dapper Server 6.06_**
*aka HowTo Install Ubuntu, Request-Tracker, Apache2, PostgreSql, Postfix*
*Oringinal at: [http://howtoforums.net/viewtopic.php?t=48](http://howtoforums.net/viewtopic.php?t=48)*

"RT is an enterprise-grade ticketing system which enables a group of people to intelligently and efficiently manage tasks, issues, and requests submitted by a community of users."
-- [http://bestpractical.com/rt/](http://bestpractical.com/rt/)

This HowTo will explain how to install request-tracker on a clean Ubuntu Dapper Server install.
It is tested on Ubuntu Dapper 6.06 and mite work with slight modifications on other versions or Debian based distros.

It also installs the Additional services required for Request-Tracker, such as Apache2 - Web Server, Postfix - Email Server (for sending emails), & PostgreSql-7.4 - Database to Store the RT information.

I create a root user as apposed to using sudo, just because i am used to it but you may add sudo in front of the commands if you prefer the sudo security default method of Ubuntu.

**To activate the root user:**
```

sudo passwd root

```

**Enable universe in your Sources.list**
```

cp -vpr /etc/apt/sources.list /etc/apt/sources.list.orig
vim /etc/apt/sources.list
#comment this:
###deb cdrom:...
#& uncomment universe sources
apt-get update
apt-get install request-tracker3.4 rt3.4-apache2 rt3.4-clients apache2-doc postfix postgresql postgresql-doc-7.4 lynx

```

In the "Postfix Configuration":
I choose "Internet Site", just because I preffer to have the system send emails without being dependant on a different mail server.
The logic behind that is because if the email Server goes down, the Ticket-Server should NOT follow.

You Should See this message after the install is done...
> 
Postfix is now set up with a default configuration.  If you need to make
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.


You will also see this:  Configuring postgresql-common
> 
Obsolete major version 7.4

  The PostgreSQL version 7.4 is obsolete, but you still have the server and/or client package installed. Please
  install the latest packages (postgresql-8.1 and postgresql-client-8.1) and upgrade your existing  clusters with
  pg_upgradecluster (see manpage).

  Please be aware that the installation of postgresql..................

  The old server and client..................

**Do not worry about it...just click OK, as RT3.4 is certified with 7.4.**


**BKUP the RT config file...I like to do this for every conf file I modify**
```

cp -vpr /etc/request-tracker3.4/RT_SiteConfig.pm /etc/request-tracker3.4/RT_SiteConfig.pm.orig

```

```

vim /etc/request-tracker3.4/RT_SiteConfig.pm

```

**Customize using the directions in the file and add this to the end of the file but before the "1;" ...**
*example config included at the end...*
```

Set($DatabaseHost   , 'localhost');
Set($DatabaseRTHost , 'localhost');

```

**Create the user for the RT database**
```

su postgres
psql -d template1
CREATE USER rtuser WITH PASSWORD 'wibble' CREATEDB NOCREATEUSER;
\q
exit

```


**Customize Postgresql permissions**
```

cp -vpr /etc/postgresql/7.4/main/pg_hba.conf /etc/postgresql/7.4/main/pg_hba.conf.orig
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

cp -vpr /etc/postgresql/7.4/main/postgresql.conf /etc/postgresql/7.4/main/postgresql.conf.orig
vim /etc/postgresql/7.4/main/postgresql.conf
make sure this is enabled
tcpip_socket = true

```

**Restart Database**
```

/etc/init.d/postgresql-7.4 restart

```


**Test db connection**
```

psql -d template1 -U rtuser -W
#enter password at the prompt, we set it to wibble in the example above
\q

```

**Create the RT DataBase**
```

/usr/sbin/rt-setup-database-3.4 --action init --dba rtuser --prompt-for-dba-password
#enter password at the prompt, we set it to wibble in the example above

```


**Configure Apache2**
```

cp -vpr /etc/apache2/sites-available/default /etc/apache2/sites-available/default.orig
vim /etc/apache2/sites-available/default

```
Add the following line to the VirtualHost section of Apache from which you wish to serve RT
```

    Include "/etc/request-tracker3.4/apache2-modperl2.conf"

```


**Enable Apache2 RewriteEngine**
```

cd /etc/apache2/mods-enabled/
ln -s ../mods-available/rewrite.load .

```

**Restart Apache**
```

/etc/init.d/apache2 force-reload

```


**_You can now login to [http://yourdomain.com/rt](http://yourdomain.com/rt)**_
using user root and password "password" (without quotation marks of course)
change this passwd asap via the Configuration menu


**_-- SSL Mode: https --**_
If you want to have Request-Tracker Secure than you are going to have to configure apache2 to run in ssl mode.
Take a look at this HowTo for more information:
[https://wiki.ubuntu.com/forum/server/apache2/SSL](https://wiki.ubuntu.com/forum/server/apache2/SSL)
I have also included my apache2 configs below.

**_-- Mail Settings --**_
This part is really network specific, but if you are going to use Request-Tracker as "support" mailbox organizer so to speak, than you need to set up the system to pull email.
One method would be using fetchmail which can grab mail from an IMAP/POP3 account and put it in the system.
The links below describe this process:
 [http://wiki.bestpractical.com/index.cgi?POP3Mailgate](http://wiki.bestpractical.com/index.cgi?POP3Mailgate)
 [http://wiki.bestpractical.com/index.cgi?ManualInstallation](http://wiki.bestpractical.com/index.cgi?ManualInstallation) (Search for "Setting Up the Mail Gateway") for the basic email settings

These are the packages if your going for the configuration with fetchmail and postfix as the outgoing smtp server
```

apt-get install fetchmail fetchmailconf fetchmail-ssl postfix ca-certificates

```

**DON'T Forget:**
you need to have "CreateTicket" permissions on "Queue General" or any queue that you throw the emails in from the user fetching the mail



**_-- Example Confs --**_


**Example Request-Tracker Config File**
------------------------------------------

**/etc/request-tracker3.4/RT_SiteConfig.pm**

```

# RT_SiteConfig.pm
#
# These are the bits you absolutely *must* edit.
#
# To find out how, please read
#   /usr/share/doc/request-tracker3.4/INSTALL.Debian

# THE BASICS:

Set($rtname, 'support.howtoforums.net');
Set($Organization, 'howtoforums.net');

Set($CorrespondAddress , 'SUPPORT-DO-NOT-REPLY@howtoforums.net');
Set($CommentAddress , 'SUPPORT-DO-NOT-REPLY@howtoforums.net');

Set($Timezone , 'Europe/London'); # obviously choose what suits you

# THE DATABASE:

Set($DatabaseType, 'Pg'); # e.g. Pg or mysql

# These are the settings we used above when creating the RT database,
# you MUST set these to what you chose in the section above.

Set($DatabaseUser , 'rtuser');
Set($DatabasePassword , 'wibble');
Set($DatabaseName , 'rtdb');

# THE WEBSERVER:

Set($WebPath , "/rt");
Set($WebBaseURL , "http://howtoforums.net");

Set($DatabaseHost   , 'localhost');
Set($DatabaseRTHost , 'localhost');

1;

```



**Example Apache2 Configuration files:**
-------------------------------------------

**/etc/apache2/sites-available/default**

```

NameVirtualHost *:80
<VirtualHost *:80>
        ServerName support.howtoforums.net
        ServerAdmin support@howtoforums.net

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

        #Redirect Request-Tracker to SSL
        RewriteEngine   on
        RewriteCond     %{SERVER_PORT} ^80$
        RewriteRule     ^/rt(.*)$ https://%{SERVER_NAME}/rt$1 [L,R]
        RewriteLog      "/var/log/apache2/rewrite.log"
        RewriteLogLevel 2

        #Request-Tracker Uncomment below if you are not redirecting and you want to answer on port 80
        #Include "/etc/request-tracker3.4/apache2-modperl2.conf"

</VirtualHost>

```


**/etc/apache2/sites-available/ssl**
```

NameVirtualHost *:443
<VirtualHost *:443>
        ServerName support.howtoforums.net
        ServerAdmin support@howtoforums.net

        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

        #Request-Tracker
        Include "/etc/request-tracker3.4/apache2-modperl2.conf"

</VirtualHost>

```

Enjoy!
Jacob
[http://howtoforums.net](http://howtoforums.net)

---

### Post by knowmad on 2006-12-29
RT can be customized by the use of the 'local' directory. This package places the local directory at /usr/local/request-tracker3.4. See the [wiki]("http://wiki.bestpractical.com/index.cgi?CleanlyCustomizeRT") for more info.

---

### Post by ChamPro on 2007-01-29
Can you give the directions for how installation would differ using MySQL instead of PostgreSQL?

---

### Post by cruizn on 2007-02-06
I, too, would love to know how to install RT 3.4 with mysql...

Can anyone help us?

---

### Post by djboonie on 2007-02-08
Trying this on Edgy, and now I cannot force-reload my apache2.

Any tips?

---

### Post by Rainmaker_mail on 2007-05-08
Hi,
I was successful in the install of RT3.6 on Ubuntu Feisty with MySQL. However, i am now lost on how to configure fetchmail to get the mail from a separate SMTP server.

I have setup my postfix as an internet with smart relay host to send the mail to my separate SMTP server. How to i then configure fetchmail to retrieve the mail ? I am confused with the instructions listed in the following URL:
[http://www-zeuthen.desy.de/ape/rt/docs/rt-FAQ.html](http://www-zeuthen.desy.de/ape/rt/docs/rt-FAQ.html)

Can anyone advice me where to create the fetchmail.rc file?

Thanks,
RM

---

### Post by Rainmaker_mail on 2007-05-08
Hi djboonie,
Perhaps you can try to run
  #sudo netstat -lnp|grep '0.0.0.0:80'
to see which process is running on the affected port

Then kill the process and start apache again
  #sudo kill <pid>

Hope this helps,
RM

---

### Post by Divan Santana on 2007-06-13
Hello, I tried this on Feisty but with RT3.6 and apache2 and postgresql .

All worked fine no errors but if I connect to [http://ipaddress/rt](http://ipaddress/rt) the directory does not exist! ..?

Any ideas anyone?? :)

---

### Post by cpetrou on 2007-07-20
Having a similar problem pulling up the [http://serverip/rt](http://serverip/rt) page. with Apache2 failing on reload.

 * Forcing reload of apache 2.0 web server... (98 )Address already in use: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                                    [fail]
Really could use the help, thanks in advance!! Weird part is Apache Default still shows up?? [http://serverip](http://serverip)

netstat -plant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 127.0.0.1:49387         0.0.0.0:*               LISTEN     4 220/hpiod
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     4 700/apache
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     4 298/cupsd
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN     4 532/postmaster
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     4 497/master
tcp        0      0 127.0.0.1:46396         0.0.0.0:*               LISTEN     4 227/python
tcp        0      0 127.0.0.1:53058         127.0.0.1:49387         ESTABLISHED4 227/python
tcp        0      0 127.0.0.1:49387         127.0.0.1:53058         ESTABLISHED4 220/hpiod
tcp6       0      0 :::5432                 :::*                    LISTEN     4 532/postmaster

---

### Post by Divan Santana on 2007-07-20
I had same problem!

Fixed it though and got rt 3.6 with apache2 working fine!
I think my problem was misconfiguration in apache confs

if you want I can post my confiurations for some files that is working...?

---

### Post by cpetrou on 2007-07-23
Any help is appriciated, post them if you would.  Thanks.

---

### Post by bmathis on 2007-07-29
Hi everyone -

I have a pre-existing server with the LAMP stack already installed, when I try and install rt3.6, it wants to install apache1 as one of the dependence's. When I made a dup setup and installed rt3.6 it broke apache2. Does anyone know how to make sure it doesnt install apache1 when apache2 is already configured and working fine?

---

### Post by Divan Santana on 2007-07-29
Yes!

Install this first i did through synaptic.
Tick rt3.6-apache2 first then request-tracker3.6

---

### Post by onesandzeros on 2008-01-20
jbaloul,

Best RT install how-to anywhere on the net, no question.  On ubuntu-server 7.10 with RT 3.6.4, it worked perfectly just by substituting 3.6 for 3.4 throughout.  The notes about the apache configuration are especially important, I think.

---

