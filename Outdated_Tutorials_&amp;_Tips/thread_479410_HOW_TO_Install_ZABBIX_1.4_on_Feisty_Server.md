---
title: "HOW TO: Install ZABBIX 1.4 on Feisty Server"
date: 2007-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by bkingx on 2007-06-20
**Intended for Zabbix 1.4 on Ubuntu Feisty Fawn 7.04**


Install pre-requisites:
Apache
MySQL-Server
PHP5
Net-Snmp libraries

**sudo aptitude install build-essentials mysql-server php5 php5-gd snmp libsnmp9-dev snmpd**

1 - Make the zabbix user and group:

**sudo adduser zabbix**
	enter in new password
	confirm
	use the remaining defaults.

Add zabbix to the admin group:

**sudo adduser zabbix admin**


2 - Download and Untar the sources:

s[B]u - zabbix
wget [http://internap.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.4.tar.gz](http://internap.dl.sourceforge.net/sourceforge/zabbix/zabbix-1.4.tar.gz)
tar zxvpf zabbix-1.4.tar.gz[/B]


3 - Create a zabbix database and populate it:
[B]
mysql -u root -p
create database zabbix;
quit;

mysql -u root -p zabbix < /home/zabbix/zabbix-1.4/create/schema/mysql.sql
mysql -u root -p zabbix < /home/zabbix/zabbix-1.4/create/data/data.sql[/B]


4 - Configure, compile and install the server:
[B]
cd zabbix-1.4/
./configure --prefix=/usr --with-mysql --with-net-snmp \
--enable-server --enable-agent &&
make
sudo make install[/B]


5 - Prepare the rest of the system:
[B]
sudo nano /etc/services[/B]

Add at the end:

[B]zabbix_agent 10050/tcp # Zabbix ports
zabbix_trap 10051/tcp[/B]

Save and exit.

[B]sudo mkdir /etc/zabbix
sudo chown -R zabbix.zabbix /etc/zabbix/
cp misc/conf/zabbix_* /etc/zabbix/[/B]

Edit /etc/zabbix/zabbix_agentd.conf:
[B]
nano /etc/zabbix/zabbix_agentd.conf[/B]

Make sure that the Server parameter points to the server address, for the agent that runs on the server it is like this:

**Server=127.0.0.1**

Edit /etc/zabbix/zabbix_server.conf:

**nano /etc/zabbix/zabbix_server.conf**

For small sites this default file will do, however if you are into tweaking your config for your 10+ hosts site, this is the place.

Change this:

[B]# Database password
# Comment this line if no password used

DBPassword=Secret[/B]

Start the server :
[B]
zabbix_server[/B]

Start the client:

**zabbix_agentd &**


6 - Configure web interface
[B]
mkdir /home/zabbix/public_html
cp -R frontends/php/* /home/zabbix/public_html/[/B]

Edit /etc/apache2/sites-enabled/000-default:

**sudo nano /etc/apache2/sites-enabled/000-default**

Work into file:

[B]Alias /zabbix/ /home/zabbix/public_html/
<Directory /home/zabbix/public_html>
  AllowOverride FileInfo AuthConfig Limit Indexes
  Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
  <Limit GET POST OPTIONS PROPFIND>
    Order allow,deny
    Allow from all
  </Limit>
  <LimitExcept GET POST OPTIONS PROPFIND>
    Order deny,allow
    Deny from all
  </LimitExcept>
</Directory>[/B]

Save and exit.

Make php.ini adjustments:

**sudo nano /etc/php5/apache2/php.ini**

Change the following values:

[B]max_execution_time = 300     ; Maximum execution time of each script, in seconds
date.timezone = America/Kentucky/Louisville[/B]
(use this url to find your correct timezone format: [http://us3.php.net/manual/en/timezones.php](http://us3.php.net/manual/en/timezones.php) )


Restart Apache:

**sudo /etc/init.d/apache2 restart**


Now point your browser to:

http://<servername or ip>/zabbix/

1. Introduction

read and click Next

2. License Agreement

Read, check 'I Agree', click Next

3. Check of Pre-Requisites

Fix any problems, click retry.  Click Next when all pre-requisites are OK.

4. Configure DB Connection

Enter appropriate settings and click Test Connection.
Click Next when OK.

5. Pre-Installation Summary

Verify installation settings, click Next.

6. Install

Click Save Configuration file and save to machine.
Copy zabbix.conf.php to /home/zabbix/public_html/conf/zabbix.conf.php

One way to do this from a desktop machine (requires ssh installed):
scp zabbix.conf.php zabbix@<serverip>:/home/zabbix/public_html/conf/

Click Retry and click Next when OK.

7. Finish

Click Finish to complete installation.


Your New Zabbix install will now be shown.

Log in with username: Admin
No Password

First go to the tab Configuration and then Hosts.

Now create a host-group, see that you can give it some templates, e.g: Application.MySQL, Host.SNMP, Host.Standalone, Host.Unix.

Then some hosts:

Select your host-group and use Link with Template Host.Unix

Now a lot of triggers are imported and the game begins.

Go to the monitoring tab and watch the latest values roll in.

For specifics on configuration, please refer to the Zabbix user manual.

[www.zabbix.com](www.zabbix.com)

---

