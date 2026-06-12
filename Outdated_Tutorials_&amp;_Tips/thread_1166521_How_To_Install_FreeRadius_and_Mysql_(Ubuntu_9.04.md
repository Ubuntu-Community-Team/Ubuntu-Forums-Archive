---
title: "How To Install FreeRadius and Mysql (Ubuntu 9.04"
date: 2009-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by interfaceupup on 2009-05-21
Ok, after a few days of frustration with googling and coming up empty handed. This is how I got freeradius and mysql to work on Ubuntu 9.04. Note if you're using server instead of desktop you are going to need to know how to add databases via cli or install mysql admin on a remote host and make mysql bind to an ip address. This doesn't cover that install. But if you get this far figuring that out is not too hard. Also, I know without doubt there are better ways to do what I have done so if you prefere some other method place it in here. 

install Mysql:
sudo apt-get install mysql-server

Install Freeradius:
sudo apt-get install freeradius freeradius-mysql

Install needed support for apache etc:
sudo apt-get install php5-mysql debhelper  libltdl3-dev libpam0g-dev libmysqlclient15-dev build-essential libgdbm-dev libldap2-dev libsasl2-dev libiodbc2-dev libkrb5-dev snmp autotools-dev dpatch  libperl-dev libtool dpkg-dev libpq-dev libsnmp-dev libssl-dev php php-mysql php-pear php-gd php-pear-DB

Install apache:
sudo apt-get install apache2

Get daloRadius:
from [http://sourceforge.net/projects/daloradius](http://sourceforge.net/projects/daloradius) 

Extract daloradius:
tar -zxvf daloradius-0.9-7.tar.gz

Move daloradius to www: 
sudo cp daloiradius-x.y-z/ /var/www -R     !!!!!!!you can change the name to something you like the x.y.z reflect the current code level. 

Set permissions:
chown www-data:www-data /var/www/daloradius-x.x-z -R

chmod 644 /var/www/daloradius-x.y-z/library/daloradius.conf

I'm not all that familiar with mysql via command line so I cheated and used mysql admin.

sudo apt-get install mysql-admin

launch MySql Administrator
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

sudo /etc/init.d/apache2 restart

Now you need to configure freeradius...joy!

use your favorite editor vi,nano cough...whatever
sudo vi /etc/freeradius/radius.conf
There will be a section in there reguarding instantiate for authorize. Just search for sql1 above that create a line with sql. Save and exit. 

Open and edit /etc/freeradius/sql.conf
edit the username, password, and make sure it is pointing to 127.0.0.1 or whatever ip your sql server is binding to.
save and exit

Open and edit /etc/freeradius/sites-enabled/default
uncomment all the sql tags in here (or the ones you want to use with mysql)

with that done make the following directory and file. Otherwise you won't authenticate.
sudo mkdir /var/log/freeradius/radacct/
sudo touch /var/log/freeradius/radacct/sql-relay

Open up your browser to [http://localhost/daloradius](http://localhost/daloradius) 

username administrator

password radius 

create a user in here
and a nas if you are using one. 

I would say use radtest but it never worked for me always had errors under 9.04 so far. I was using a Cisco ASA which has a test feature for AAA. But use what ever you are trying to configure with aaa you should now be able to authenticate. 

If you want to run freeradius in test mode so you can see some errors or successes on your console.

Stop freeradius daemon
sudo /etc/init.d/freeradius stop

Start freeradius in debug mode
sudo freeradius -X

You should be good now. If not you are on your own...sorry.

---

### Post by amgnix on 2009-09-01
Excellent Post. Saved me a load of time.
Thanks
A

---

