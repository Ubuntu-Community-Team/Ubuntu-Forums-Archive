---
title: "xubuntu with LAMP, freeradius, dolaradius"
date: 2009-04-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Stecha on 2009-04-06
How to setup web management with Daloradius
----------------------------------------------------------------------------------------------

--------------------------------------------------------------------------------------
First we need to make sure we have downloaded all the correct files.
---------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------

Check to see if you have the at least the minimum installed.

1. xubuntu 8.10 -- This is what we used at the time of writing this article.

2. LAMP -- Linux, Apach2, MySQL, PHP

3. php-pear, php5-gd, php-DB -- You must have these files installed for daloradius to function correctly.
   sudo apt-get install php-pear php5-gd php-DB

4. freeradius  -- This has to be installed for production WISP, but you can evaluate Daloradius without it.
   sudo apt-get install freeradius





The latest stable release is version daloradius-0.9-8

Get hold of the it from [http://sourceforge.net/projects/daloradius](http://sourceforge.net/projects/daloradius).
----------------------------------------------------------------------------------------------
Go to the directory where you downloaded daloradius-0.9-8.tar.gz to and extract it with the following code.
----------------------------------------------------------------------------------------------

tar -zxvf daloradius-0.9-8.tar.gz

----------------------------------------------------------------------------------------------
Copy the extracted folder to /var/www
----------------------------------------------------------------------------------------------

cp daloradius-0.9-8/ /var/www -R

----------------------------------------------------------------------------------------------
Change permissions and ownership:
----------------------------------------------------------------------------------------------

chown www-data:www-data /var/www/daloradius-0.9-8 -R

chmod 777 /var/www/daloradius-0.9-8/library/daloradius.conf.php -- Be sure to change this back to 644 when done.

-----------------------------------------------------------------------------------------------
Daloradius needs to add a few more tables to the radius database we already created earlier.
-----------------------------------------------------------------------------------------------

sudo mysql -uroot -ppassword radius < /var/www/daloradius-0.9-8/contrib/db/mysql-daloradius.sql -- Change password to reflect your settings.

-----------------------------------------------------------------------------------------------
Now, simply adjust the MySQL database information in the DaloRadius config file.
-----------------------------------------------------------------------------------------------

sudo vim /var/www/daloradius-0.9-8/library/daloradius.conf.php


Fill in the database details, a few important parameters are listed below:

CONFIG_DB_ENGINE = mysql
CONFIG_DB_HOST = 127.0.0.1
CONFIG_DB_USER = radius
CONFIG_DB_PASS = radpass
CONFIG_DB_NAME = radius
......................................................
Do not worry about settings at the bottom of the file.
......................................................

Save the file and exit.

------------------------------------------------------------------------------------------------
Set up the apache server.
------------------------------------------------------------------------------------------------

Create a new file in /etc/apache2/sites-enabled/ 
sudo vim /etc/apache2/sites-enabled/daloradius-0.9-8 
---------------------------------------------------------

Add this to the the file (customize to your likings):


Alias /myradius "/var/www/daloradius-0.9-8/"

Options None
order deny,allow
deny from all
allow from 127.0.0.1
allow from


Save and exit.

------------------------------------------------------------------------------------------------
Restart the httpd server:
------------------------------------------------------------------------------------------------

sudo /etc/init.d/apache2 restart

------------------------------------------------------------------------------------------------
Fire up Firefox (or any other borowser) and go to the URL [http:///myradius](http:///myradius).
------------------------------------------------------------------------------------------------

Log in with the administrator for management:
username: administrator
password: radius

1. Change the login information first (info is located in the operator table).

2. Make sure to go to the Config tab then on the left select Database Settings then select tables. Change usergroup from usergroup to radusergroup.

   This will save some of the head aches I had getting this set up right.

--------------------------------------------------------------------------------------------------

Congratulations you are done and should now be able to auth via radius users around your network.

Next you will want to set up eap/ttls. But that will be another post.

---

