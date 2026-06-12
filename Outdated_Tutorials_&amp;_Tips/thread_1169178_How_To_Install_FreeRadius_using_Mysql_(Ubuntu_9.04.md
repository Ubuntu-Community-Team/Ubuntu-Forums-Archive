---
title: "How To Install FreeRadius using Mysql (Ubuntu 9.04)"
date: 2009-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by interfaceupup on 2009-05-24
Ok, after a few days of frustration with googling and coming up empty handed. This is how I got freeradius and mysql to work on Ubuntu 9.04. 

install Mysql:
```
sudo apt-get install mysql-server
```Install Freeradius:
```
sudo apt-get install freeradius freeradius-mysql
```Install needed support for apache etc:
```
sudo apt-get install php5-mysql debhelper  libltdl3-dev libpam0g-dev libmysqlclient15-dev build-essential libgdbm-dev libldap2-dev libsasl2-dev libiodbc2-dev libkrb5-dev snmp autotools-dev dpatch  libperl-dev libtool dpkg-dev libpq-dev libsnmp-dev libssl-dev php php-mysql php-pear php-gd php-pear-DB
```Install apache:
```
sudo apt-get install apache2
```Get daloRadius:
```
from [http://sourceforge.net/projects/daloradius](http://sourceforge.net/projects/daloradius)
``` 

Extract daloradius:
```
tar -zxvf daloradius-0.9-7.tar.gz
```Move daloradius to www: 
```
sudo cp daloiradius-x.y-z/ /var/www -R     
```!!!!!!!you can change the name to something you like the x.y.z reflect the current code level. 

Set permissions:
```
chown www-data:www-data /var/www/daloradius-x.x-z -R
``````
chmod 644 /var/www/daloradius-x.y-z/library/daloradius.conf
```I'm not all that familiar with mysql via command line so I cheated and used mysql admin.

```
sudo apt-get install mysql-admin
```launch MySql Administrator
Go to catalogs create a new database (schema) called radius
Then go to user administration and create a user and password
Then under the User Accounts section make sure to add host 127.0.0.1 if your mysql is binding to that address if you don't know it most likely is.
Then select schema priviledges in there add all the priviledges for that schema to that user. 
Click apply you can exit now.

launch Mysql Querry Browser
Open the sql script located in /var/www/daloradius-x.y-z/contrib/db/fr2-mysql-daloradius-and-freeradius.sql
Then click on execute. This will build your tables for free radius and for daloradius.

Configure the daloradius.conf file in /var/www/daloradius/library/daloradius.conf with the appropriate database information

restart apache

```
sudo /etc/init.d/apache2 restart
```Now you need to configure freeradius...joy!

use your favorite editor vi,nano cough...whatever
```
sudo vi /etc/freeradius/radius.conf
```There will be a section in there reguarding instantiate for authorize. Just search for sql1 above that create a line with sql. Save and exit. 

Open and edit ```
/etc/freeradius/sql.conf
```
edit the username, password, and make sure it is pointing to 127.0.0.1 or whatever ip your sql server is binding to.
save and exit

Open and edit ```
/etc/freeradius/sites-enabled/default
```
uncomment all the sql tags in here (or the ones you want to use with mysql)

with that done make the following directory and file. Otherwise you won't authenticate.
```
sudo mkdir /var/log/freeradius/radacct/
``````
sudo touch /var/log/freeradius/radacct/sql-relay
```Open up your browser to [http://localhost/daloradius](http://localhost/daloradius) 

username administrator

password radius 

create a user in here
and a nas if you are using one. 

I would say use radtest but it never worked for me always had errors under 9.04 so far. I was using a Cisco ASA which has a test feature for AAA. But use what ever you are trying to configure with aaa you should now be able to authenticate. 

If you want to run freeradius in test mode so you can see some errors or successes on your console.

Stop freeradius daemon
```
sudo /etc/init.d/freeradius stop
```Start freeradius in debug mode
```
 sudo freeradius -X
```You should be good now. If not I highly recommend starting freeradius in debug mode and reviewing the issues. I'll try to help when I can.

---

### Post by koelneruwe on 2009-08-03
Hi,
I cannot find 
/etc/freeradius/sites-enabled/default

Any idea?

---

### Post by kevdog on 2009-08-03
So the point of this project was just to allow the freeradius server to provide authentication for the various users?  Correct?

---

### Post by raj4483 on 2009-09-10
i am installed FreeRadius following  procedure, but i can't find /var/www/daloradius-0.9-8/library/daloradius.conf

---

### Post by koelneruwe on 2009-10-07
Its now 
daloradius.conf.php

---

### Post by DemaSRV on 2009-10-10
I'm having an issue when I try to build the tables using the query browser.   It's saying 


```
Error while executing query: CREATE TABLE radacct (
  radacctid bigint(21) NOT NULL auto_increment,
  acctsessionid varchar(32) NOT NULL default '',
  acctuniqueid varchar(32) NOT NULL default '',
  username varchar(64) NOT NULL default '',
  groupname varchar(64) NOT NULL default '',
  realm varchar(64) default '',
  nasipaddress varchar(15) NOT NULL default '',
  nasportid varchar(15) default NULL,
  nasporttype varchar(32) default NULL,
  acctstarttime datetime NULL default NULL,
  acctstoptime datetime NULL default NULL,
  acctsessiontime int(12) default NULL,
  acctauthentic varchar(32) default NULL,
  connectinfo_start varchar(50) default NULL,
  connectinfo_stop varchar(50) default NULL,
  acctinputoctets bigint(20) default NULL,
  acctoutputoctets bigint(20) default NULL,
  calledstationid varchar(50) NOT NULL default '',
  callingstationid varchar(50) NOT NULL default '',
  acctterminatecause varchar(32) NOT NULL default '',
  servicetype varchar(32) default NULL,
  framedprotocol varchar(32) default NULL,
  framedipaddress varchar(15) NOT NULL default '',
  acctstartdelay int(12) default NULL,
  acctstopdelay int(12) default NULL,
  xascendsessionsvrkey varchar(10) default NULL,
  PRIMARY KEY  (radacctid),
  KEY username (username),
  KEY framedipaddress (framedipaddress),
  KEY acctsessionid (acctsessionid),
  KEY acctsessiontime (acctsessiontime),
  KEY acctuniqueid (acctuniqueid),
  KEY acctstarttime (acctstarttime),
  KEY acctstoptime (acctstoptime),
  KEY nasipaddress (nasipaddress)
) :
No database selected (errno: 1046)
Click 'Ignore' if you'd like to have this error ignored until the end of the script.
```

---

### Post by maaf on 2009-10-18
hi all
is this package support ssl

---

### Post by interfaceupup on 2009-10-18
Sorry all, I have not been paying close attention to this thread. I moved on from using radius as it just wasn't as robust as tacacs+. Seeing as I am working on my CCIE I am sticking strictly to Cisco centric systems. Not that I think radius wouldn't work I just want to stick as close to cisco specifics as possible. Also, I'm not sure if daloradius has made any changes in order to perform use https.

---

### Post by Ett_tingest on 2009-10-22
I seem to have a problem following this tutorial...
 
i need to find /var/www/daloradius-0.9-7/contrib/db/fr2-mysql-daloradius-and-freeradius.sql

Im using same version of daloradius as the one writing this tutorial so how come i cant find this script? Have something gone wrong when i downloaded daloradius? Since i cant find it even in the compressed folder.

---

### Post by Ett_tingest on 2009-10-27
Okay... So did you get this solution to work with OpenSSL support?
 
I have had trouble to get OpenSSL to work with the installation that comes with Ubuntus Synaptic Package Manager. I´ve read that it do not have OpenSSL support and therefore you cannot use PEAP authentication? Is this correct?

---

### Post by interfaceupup on 2009-11-20
No I never got openssl to work with that version.

---

### Post by interfaceupup on 2009-11-20
> **Ett_tingest said:**
> I seem to have a problem following this tutorial...
 
i need to find /var/www/daloradius-0.9-7/contrib/db/fr2-mysql-daloradius-and-freeradius.sql
 
Im using same version of daloradius as the one writing this tutorial so how come i cant find this script? Have something gone wrong when i downloaded daloradius? Since i cant find it even in the compressed folder.
 
 
Well huh, it should be thre it's been quite a while since I messed with it like I sad before I'm studying for my CCIE so I have sort of fallen off the radius band wagon. My studies have taken up a lot of my time. I can look and see if it;s still in my packages if so I can forward it on to you.

---

### Post by Ett_tingest on 2009-11-20
> **interfaceupup said:**
> No I never got openssl to work with that version.
 
 
I thought so, but then you maybe have some hints about this then =)
 
I have made an own build that got OpenSSL support but I also need to get MySQL to work with that build.
 
What I have done so far to get OpenSSL support for FreeRadius 2.1.7 with OpenSSL 0.9.8l is that when i do the ./configure command i also add "--with-openssl --with-openssl-includes=/blablabla --with-openssl-libraries=/blablabla" but I dont seem to have the module for mysql installed or something like that since i do not get my db to work towards the radius server. Do you know if I have missed something?
 
Best Regards/ Peter

---

### Post by oprogue on 2010-02-14
I've toyed with trying to get freeradius configured without success.  For whatever the reason I an error during the initial installation of php:

following the command: 

sudo apt-get install php5-mysql debhelper  libltdl3-dev libpam0g-dev libmysqlclient15-dev build-essential libgdbm-dev libldap2-dev libsasl2-dev libiodbc2-dev libkrb5-dev snmp autotools-dev dpatch  libperl-dev libtool dpkg-dev libpq-dev libsnmp-dev libssl-dev php php-mysql php-pear php-gd php-pear-DB

Everything goes ok until the end:

[INDENT]dpatch set to manually installed.
[INDENT][/INDENT]dpkg-dev is already the newest version.
[INDENT][/INDENT]dpkg-dev set to manually installed.
[INDENT][/INDENT]E: Couldn't find package php[/INDENT]

Seemingly unrelated I am unable to find the freeradius conf files, the default dir is suppose to be /usr/local/etc/raddb  I've scanned the system files without success.  

I'm attempting this on 9.04; would I have more success if I upgrade to 9.10? Would I be better to use radiusd-livingston, xtradius, or yardradius in getting a hotspot AAA configuration setup?

Thanks in advance!

---

### Post by Mellow Heart on 2011-01-28
[CENTER]please help me To complete install free radius

when i need to execute fr2-mysql-daloradius-and-freeradius.sql in mysql qeury browser :

this error show to me

```
Error while executing query: CREATE TABLE radacct (
radacctid bigint(21) NOT NULL auto_increment,
acctsessionid varchar(32) NOT NULL default '',
acctuniqueid varchar(32) NOT NULL default '',
username varchar(64) NOT NULL default '',
groupname varchar(64) NOT NULL default '',
realm varchar(64) default '',
nasipaddress varchar(15) NOT NULL default '',
nasportid varchar(15) default NULL,
nasporttype varchar(32) default NULL,
acctstarttime datetime NULL default NULL,
acctstoptime datetime NULL default NULL,
acctsessiontime int(12) default NULL,
acctauthentic varchar(32) default NULL,
connectinfo_start varchar(50) default NULL,
connectinfo_stop varchar(50) default NULL,
acctinputoctets bigint(20) default NULL,
acctoutputoctets bigint(20) default NULL,
calledstationid varchar(50) NOT NULL default '',
callingstationid varchar(50) NOT NULL default '',
acctterminatecause varchar(32) NOT NULL default '',
servicetype varchar(32) default NULL,
framedprotocol varchar(32) default NULL,
framedipaddress varchar(15) NOT NULL default '',
acctstartdelay int(12) default NULL,
acctstopdelay int(12) default NULL,
xascendsessionsvrkey varchar(10) default NULL,
PRIMARY KEY (radacctid),
KEY username (username),
KEY framedipaddress (framedipaddress),
KEY acctsessionid (acctsessionid),
KEY acctsessiontime (acctsessiontime),
KEY acctuniqueid (acctuniqueid),
KEY acctstarttime (acctstarttime),
KEY acctstoptime (acctstoptime),
KEY nasipaddress (nasipaddress)
) :
No database selected (errno: 1046)
Click 'Ignore' if you'd like to have this error ignored until the end of the script
```


and in this step :

```
sudo vi /etc/freeradius/radius.conf

There will be a section in there reguarding instantiate for authorize. Just search for sql1 above that create a line with sql. Save and exit
```

In this step what you want me to write in this file ???

thank you
[/CENTER]

---

### Post by Mellow Heart on 2011-01-29
[CENTER]anybody answer me ??
 
pazzzz[/CENTER]

---

### Post by okman on 2011-03-03
Hi Mellow Heart.
I guess that you havent received answer yet is because the error you are getting is quite explanatory - No database selected!

Create a database ( I guess youre using phpMyadmin ?), open it and just then try to execute the querry to create a table ...

hope i helped

---

### Post by pstacks on 2011-03-15
Anybody have an answer as to why I'm getting an internal server error when attempting login from daloradius admin page.  Following is the page response:

The website encountered an error while retrieving [http://ubu104/daloradius-0.9-8/dologin.php](http://ubu104/daloradius-0.9-8/dologin.php). It may be down for maintenance or configured incorrectly.

HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request.

No problems with the install that I saw.

After login problem, I ran freerad in debug and got this:


root@ubu104:/tmp# sudo freeradius -X
FreeRADIUS Version 2.1.9, for host i686-pc-linux-gnu, built on Jun 21 2010 at 19:17:04
Copyright (C) 1999-2009 The FreeRADIUS server project and contributors.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
You may redistribute copies of FreeRADIUS under the terms of the
GNU General Public License v2.
Starting - reading configuration files ...
including configuration file /etc/freeradius/radiusd.conf
including configuration file /etc/freeradius/proxy.conf
including configuration file /etc/freeradius/clients.conf
including files in directory /etc/freeradius/modules/
including configuration file /etc/freeradius/modules/sradutmp
including configuration file /etc/freeradius/modules/realm
including configuration file /etc/freeradius/modules/logintime
including configuration file /etc/freeradius/modules/acct_unique
including configuration file /etc/freeradius/modules/unix
including configuration file /etc/freeradius/modules/files
including configuration file /etc/freeradius/modules/smbpasswd
including configuration file /etc/freeradius/modules/passwd
including configuration file /etc/freeradius/modules/sql_log
including configuration file /etc/freeradius/modules/wimax
including configuration file /etc/freeradius/modules/mac2ip
including configuration file /etc/freeradius/modules/echo
including configuration file /etc/freeradius/modules/checkval
including configuration file /etc/freeradius/modules/digest
including configuration file /etc/freeradius/modules/pap
including configuration file /etc/freeradius/modules/always
including configuration file /etc/freeradius/modules/ntlm_auth
including configuration file /etc/freeradius/modules/mac2vlan
including configuration file /etc/freeradius/modules/krb5
including configuration file /etc/freeradius/modules/ippool
including configuration file /etc/freeradius/modules/mschap
including configuration file /etc/freeradius/modules/chap
including configuration file /etc/freeradius/modules/expiration
including configuration file /etc/freeradius/modules/detail.log
including configuration file /etc/freeradius/modules/attr_filter
including configuration file /etc/freeradius/modules/preprocess
including configuration file /etc/freeradius/modules/ldap
including configuration file /etc/freeradius/modules/linelog
including configuration file /etc/freeradius/modules/smsotp
including configuration file /etc/freeradius/modules/etc_group
including configuration file /etc/freeradius/modules/otp
including configuration file /etc/freeradius/modules/detail
including configuration file /etc/freeradius/modules/perl
including configuration file /etc/freeradius/modules/policy
including configuration file /etc/freeradius/modules/radutmp
including configuration file /etc/freeradius/modules/pam
including configuration file /etc/freeradius/modules/cui
including configuration file /etc/freeradius/modules/sqlcounter_expire_on_login
including configuration file /etc/freeradius/modules/exec
including configuration file /etc/freeradius/modules/inner-eap
including configuration file /etc/freeradius/modules/attr_rewrite
including configuration file /etc/freeradius/modules/expr
including configuration file /etc/freeradius/modules/counter
including configuration file /etc/freeradius/modules/detail.example.com
including configuration file /etc/freeradius/eap.conf
including configuration file /etc/freeradius/policy.conf
including files in directory /etc/freeradius/sites-enabled/
including configuration file /etc/freeradius/sites-enabled/inner-tunnel
including configuration file /etc/freeradius/sites-enabled/default
main {
        user = "freerad"
        group = "freerad"
        allow_core_dumps = no
}
including dictionary file /etc/freeradius/dictionary
main {
        prefix = "/usr"
        localstatedir = "/var"
        logdir = "/var/log/freeradius"
        libdir = "/usr/lib/freeradius"
        radacctdir = "/var/log/freeradius/radacct"
        hostname_lookups = no
        max_request_time = 30
        cleanup_delay = 5
        max_requests = 1024
        pidfile = "/var/run/freeradius/freeradius.pid"
        checkrad = "/usr/sbin/checkrad"
        debug_level = 0
        proxy_requests = yes
 log {
        stripped_names = no
        auth = no
        auth_badpass = no
        auth_goodpass = no
 }
 security {
        max_attributes = 200
        reject_delay = 1
        status_server = yes
 }
}
radiusd: #### Loading Realms and Home Servers ####
 proxy server {
        retry_delay = 5
        retry_count = 3
        default_fallback = no
        dead_time = 120
        wake_all_if_all_dead = no
 }
 home_server localhost {
        ipaddr = 127.0.0.1
        port = 1812
        type = "auth"
        secret = "testing123"
        response_window = 20
        max_outstanding = 65536
        require_message_authenticator = no
        zombie_period = 40
        status_check = "status-server"
        ping_interval = 30
        check_interval = 30
        num_answers_to_alive = 3
        num_pings_to_alive = 3
        revive_interval = 120
        status_check_timeout = 4
        irt = 2
        mrt = 16
        mrc = 5
        mrd = 30
 }
 home_server_pool my_auth_failover {
        type = fail-over
        home_server = localhost
 }
 realm example.com {
        auth_pool = my_auth_failover
 }
 realm LOCAL {
 }
radiusd: #### Loading Clients ####
 client localhost {
        ipaddr = 127.0.0.1
        require_message_authenticator = no
        secret = "testing123"
        nastype = "other"
 }
radiusd: #### Instantiating modules ####
 instantiate {
 Module: Linked to module rlm_exec
 Module: Instantiating exec
  exec {
        wait = no
        input_pairs = "request"
        shell_escape = yes
  }
 Module: Linked to module rlm_expr
 Module: Instantiating expr
 Module: Linked to module rlm_expiration
 Module: Instantiating expiration
  expiration {
        reply-message = "Password Has Expired  "
  }
 Module: Linked to module rlm_logintime
 Module: Instantiating logintime
  logintime {
        reply-message = "You are calling outside your allowed timespan  "
        minimum-timeout = 60
  }
ERROR: Cannot find a configuration entry for module "sql".
root@ubu104:/tmp#

---

