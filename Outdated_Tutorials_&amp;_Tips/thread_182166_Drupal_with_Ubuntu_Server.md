---
title: "Drupal with Ubuntu Server"
date: 2006-05-25
forum: Outdated Tutorials &amp; Tips
---

### Post by sto6ma9ch on 2006-05-25
**Installing Drupal on Ubuntu Dapper**
Drupal is a very versatile content management system (CMS) that allows a user to set up a dynamic website with relative ease. I chose Drupal for this HOWTO because of it's extendibility. A user can add various modules to his/her site to add, for example, a photo/video manager, a collaborative book, or movie reviews. This Drupal configuration will use Apache2 as the web server with PHP4 support, and MySQL for the database. Let's get started!

*Set Up The Base System*
The first thing to do is to install Ubuntu Dapper server onto the machine. There are a great many resources available to guide users through installing Ubuntu, so I'll point users toward their website for assistance with this step. Once Ubuntu Dapper is installed, we'll need to edit apt's sources list file to comment out the CD-ROM source and add the universe repositories:
```
sudo nano /etc/apt/sources.list
```
Find the line that starts with this:
```
deb cdrom:[Ubuntu 6.06 _Dapper Drake_ ...
```
Put a comment symbol in front of the line so that apt won't use this source:
```
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ ...
```
Find the lines that look like this:
```
# deb http://us.archive.ubuntu.com/ubuntu dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu dapper universe
```
Make them look like this by removing the comment symbol:
```
deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe
```
Press Ctrl+X to exit nano, type "Y" to save your changes, and press Enter to accept the filename. Now run these two commands to refresh the list of available packages and to make sure that your system is up-to-date:
```
sudo apt-get update
sudo apt-get upgrade
```

*Install Apache2*
Now we need to start installing the core components of our website. The first piece we'll install is the Apache web server. Type this:
```
sudo apt-get install apache2
```
To verify that the web server is up and running, point another machine's web browser to this computer using "http://ip_address". You should see Apache's version number at the bottom of this page. If you don't, you may need to verify that there are no firewalls or routers in between you and this machine.

*Install PHP4*
Easy enough so far, right? Let's add PHP support to our site. To do so, type the following:
```
sudo apt-get install libapache2-mod-php4
```
Now we'll need to make sure that PHP support is enabled for our site. This can be done by verifying that a line in /etc/apache2/apache2.conf is uncommented. Type the following:
```
sudo nano /etc/apache2/apache2.conf
```
Find the lines that look like this:
```
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps
```
Uncomment these lines so that they look like this:
```
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps
```
Press Ctrl+X to exit nano, type "Y" to save your changes, and press Enter to accept the filename. To test your installation of PHP, you can point a web browser to this computer using "http://ip_address". At the bottom of this page, you should see that PHP's version number has been appended to Apache's version number. If you don't see this, you may want to check PHP support.

*Install MySQL*
Now let's install MySQL. Issue the following command:
```
sudo apt-get install mysql-server
```
Once that's finished, the next step is to set the database password for the "root" database user (this is not the local machine's root account). Type the following:
```
mysql -u root
```
You should get a welcome message and a MySQL prompt. Continue typing the following:
```
mysql> UPDATE mysql.user SET Password=PASSWORD('your_new_password')
WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> quit
```
Now we need to create a new database for Drupal. In this example we'll name the database "drupal".
```
mysqladmin -u root -p create drupal
```
Now the database should be ready. If any error messages appear during the database build, you may need to try reinstalling the mysql-server package.

*Install Drupal*
This step will install the Drupal site files and any remaining dependencies.
```
sudo apt-get install drupal
```
Our website's files have been installed into /usr/share/drupal, so let's create a symbolic link to that directory in our website's document root, /var/www:
```
sudo ln -s /usr/share/drupal /var/www/drupal
```
This allows us to access our Drupal pages without a lot of administrative overhead. For this next step, we're going to set up the "drupal" database scheme. Normally this would be a very tedious process. Fortunately, Drupal comes with a script to help automate this. Instead of manually creating the schema, just type in this command:
```
mysql -u root -p drupal < /var/www/drupal/database/database.mysql
```
The next step is to create a PHP configuration file so that Drupal knows to connect to our "drupal" database. That's the first line. The second line will create the domain configuration:
```
sudo nano /etc/drupal/conf.php
```
Add these lines to your new file:
```
<?php
$db_url = "mysql://root:your_database_password@localhost/drupal";
$base_url = "http://drupal_server's_ip_address/drupal";
?>
```
Again, this configuration will only be good for your internal LAN. To make this server work externally, use this:
```
<?php
$db_url = "mysql://root:your_database_password@localhost/drupal";
$base_url = "http://your_FullyQualifiedDomainName/drupal";
?>

```
Now let's make sure that PHP can talk to MySQL. Type the following:
```
sudo nano /etc/php4/apache2/php.ini
```
Locate the line in the "Dynamic Extensions" section that looks like this:
```
;extension=mysql.so
```
Uncomment this line by changing it to this:
```
extension=mysql.so
```
For those of you who will be adding the photo/video module to your site, uncomment this line as well (trust me, you don't want to start hunting for this one after the fact):
```
;extension=gd.so
```
... and make it look like this:
```
extension=gd.so
```
Press Ctrl+X to exit nano, type "Y" to save your changes, and press Enter to
accept the filename. We're almost finished. The next thing to do is to restart the web service, and you're ready. Do it thus-ly:
```
sudo /etc/init.d/apache2 restart
```
The installation and setup of your very own Drupal CMS is complete. The next step is to crack open a beer, point your browser to http://you_drupal's_ip_address/drupal, and start tweaking it. Be sure to check out Drupal's modules page for ideas on extending the functionality of your server.

---

### Post by adamkane on 2006-05-27
How to install Apache/MySQL/PHP (the easy way) in preparation for Drupal:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by sto6ma9ch on 2006-05-27
adamkane:

Thanks for the addition. I wanted to show users each step individually in this HOWTO to illustrate how each component works together.

---

### Post by adamkane on 2006-05-27
Apologies for horning in. Nice howto. :)

---

### Post by mtron on 2006-05-29
thanks a lot! durpal is for me much easier to adjust than the other CMS´es like mambo (or joomla)

nice howto, but i would add that this apache conf is not recommended for a running system (it's ok for development)

---

### Post by sto6ma9ch on 2006-05-29
mtron: Thanks! What tweaks to apache.conf would you suggest to make this HOWTO better for a publicly-accessible server?

---

### Post by macewan on 2006-05-30
nice howto, thanks for taking the time to post this *worth the Google bookmark*

---

### Post by macewan on 2006-06-08
just got around to testing it and it seems to work fine.

---

### Post by Janus on 2006-06-09
[QUOTE=sto6ma9ch]**Installing Drupal on Ubuntu Breezy**
Now we'll need to make sure that PHP support is enabled for our site. This can be done by verifying that a line in /etc/apache2/apache2.conf is uncommented. Type the following:
```
sudo nano /etc/apache2/apache2.conf
```
Find the lines that look like this:
```
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps
```
Uncomment these lines so that they look like this:
```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```
[/QUOTE]
If you ad .phtml to
```
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps
```
so it looks like this
```
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps
```

made it work for me in dapper. I followed this how to, but then if I surfed to [http://localhost/drupal](http://localhost/drupal) firefox would always ask me to download some .phtml file. By just adding .phtml this was fixed and I could resume with drupal

---

### Post by GreenLight on 2006-06-09
I tried to follow this for Dapper, and I get stuck with this error in the mysql installation:

*Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1_all.deb)  MD5Sum mismatch*

There was a problem with libplrpc-perl_0.2017-1_all.deb  
Any ideas about a fix for this?

---

### Post by sto6ma9ch on 2006-06-09
GreenLight: That message means that the download of that particular package went awry. Try running the following commands:
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install mysql-server
```
Apt will then try re-downloading the package. Let us know how it goes from there.

---

### Post by sto6ma9ch on 2006-06-09
Janus: Thanks for researching the fix for the .phtml extensions! I'll try to get around to adding that to the HOWTO.

---

### Post by GreenLight on 2006-06-12
[QUOTE=sto6ma9ch]GreenLight: That message means that the download of that particular package went awry. Try running the following commands:
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install mysql-server
```
Apt will then try re-downloading the package. Let us know how it goes from there.[/QUOTE]
I followed your instructions exactly, but get the same error:
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1_all.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```It does not appear to attempt to re-load the package, the error occurrs immediately.

---

### Post by sto6ma9ch on 2006-06-12
GreenLight: Hmm, try this:
```
sudo apt-get autoclean
sudo apt-get install mysql-server
```
Let us know what happens after that.

---

### Post by GreenLight on 2006-06-13
[QUOTE=sto6ma9ch]GreenLight: Hmm, try this:
```
sudo apt-get autoclean
sudo apt-get install mysql-server
```
Let us know what happens after that.[/QUOTE]
Same result:```

<blah>:~$ sudo apt-get autoclean
Password:
Reading package lists... Done
Building dependency tree... Done
<blah>:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libdbd-mysql-perl libdbi-perl libplrpc-perl mysql-client-5.0 mysql-server-5.0
Suggested packages:
  dbishell libcompress-zlib-perl
Recommended packages:
  mailx
The following NEW packages will be installed:
  libdbd-mysql-perl libdbi-perl libplrpc-perl mysql-client-5.0 mysql-server mysql-server-5.0
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 658kB/28.5MB of archives.
After unpacking 65.6MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://us.archive.ubuntu.com dapper/main libplrpc-perl 0.2017-1 [35.0kB]
Get:2 http://us.archive.ubuntu.com dapper/main libdbi-perl 1.50-1 [623kB]
Fetched 658kB in 1m6s (9891B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1_all.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by sto6ma9ch on 2006-06-13
GreenLight: That last "autoclean" command should have erased the old downloaded files, but it looks like that package wasn't old enough. Let's try erasing all of the previously downloaded files with the "clean" command:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install mysql-server
```
If this doesn't work, then I'm out of ideas. Does anyone else have any sugggestions?

---

### Post by GreenLight on 2006-06-13
[QUOTE=sto6ma9ch]GreenLight: That last "autoclean" command should have erased the old downloaded files, but it looks like that package wasn't old enough. Let's try erasing all of the previously downloaded files with the "clean" command:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install mysql-server
```
If this doesn't work, then I'm out of ideas. Does anyone else have any sugggestions?[/QUOTE]
Thanks for all of your help -- I still get the same error with the latest guidance.
I am sure that I must be an anomaly, because surely SOMEONE has been able to install mysql-server in Dapper...

---

### Post by sto6ma9ch on 2006-06-14
GreenLight: One last suggestion -
Try downloading just that libplrpc-perl package by itself and installing it without the help of apt like so ...
```
wget http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1_all.deb
sudo dpkg -i libplrpc-perl_0.2017-1_all.deb

```
This won't do dependency checking, so you may get an error about another package that needs to be installed first. If you do get a dependency error, try using the same method to install the dependency. 

Provided that that works, try executing this command:
```
sudo apt-get install mysql-server
```

Keep us posted.

---

### Post by Simian on 2006-06-15
thanks for the How-To. Normally I would have jsut set up drupal in the /var/www directory but creating a link seems like a better way to do it.

---

### Post by GreenLight on 2006-06-15
[QUOTE=sto6ma9ch]GreenLight: One last suggestion -
Try downloading just that libplrpc-perl package by itself and installing it without the help of apt like so ...
```
wget http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libplrpc-perl/libplrpc-perl_0.2017-1_all.deb
sudo dpkg -i libplrpc-perl_0.2017-1_all.deb

```
This won't do dependency checking, so you may get an error about another package that needs to be installed first. If you do get a dependency error, try using the same method to install the dependency. 

Provided that that works, try executing this command:
```
sudo apt-get install mysql-server
```

Keep us posted.[/QUOTE]
Well, I tried doing what you had suggested:
```
dpkg: error processing libplrpc-perl_0.2017-1_all.deb (--install):
 failed to open package info file `/var/lib/dpkg/tmp.ci/control' for reading: No such file or directory
Errors were encountered while processing:
 libplrpc-perl_0.2017-1_all.deb
```

---

### Post by sto6ma9ch on 2006-06-15
GreenLight: I've never seen that dpkg error message before now. It sounds like some package never got fully installed. Can you try reinstalling dpkg?
```
sudo apt-get install --reinstall dpkg
```
I'm only guessing at this point. Is there anyone else that can help us out?

---

### Post by sangs on 2006-06-18
Great instructions :)

Sangs...

---

### Post by stubby on 2006-06-19
any chance to get drupal to work with php5?

---

### Post by sto6ma9ch on 2006-07-30
I just wrote out the ***first untested draft*** of a BASH script that should hopefully automate the entire setup process for Drupal. My scripting skills, however, are beneath the scope of this. I'm not even sure that some of the syntax is correct. If anyone has any recommendations or would like to help, please let me know.
```
#!/bin/bash

# Get superuser privileges

# sudo su

# Add multiverse repositories to /etc/apt/sources.list

echo
echo Setting up sources.list file ...
echo

mv /etc/apt/sources.list /etc/apt/sources.list.bak
touch /etc/apt/sources.list
echo ## Add comments (##) in front of any line to remove it from being checked. >> /etc/apt/sources.list
echo ## Use the following sources.list at your own risk. >> /etc/apt/sources.list
echo deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse >> /etc/apt/sources.list
echo ## MAJOR BUG FIX UPDATES produced after the final release >> /etc/apt/sources.list
echo deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse >> /etc/apt/sources.list
echo ## UBUNTU SECURITY UPDATES >> /etc/apt/sources.list
echo deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse >> /etc/apt/sources.list

# Update apt package cache

echo
echo Updating apt ...
echo

apt-get update

# Upgrade Ubuntu installation

echo
echo Upgrading your Ubuntu installation ...
echo

apt-get upgrade -y

# Install required servers/software

echo
echo Installing required services and software ...
echo

apt-get install apache2 libapache2-mod-php4 mysql-server drupal -y --force-yes -qq

# Configure services

echo
echo Configuring Apache2 ...
echo

sed -e 's/#AddType application/x-httpd-php .php/AddType application/x-httpd-php .php .phtml/g' /etc/apache2/apache2.conf

echo
echo Configuring MySQL ...
echo

# -----------------------------------------------------
# Get info on setting root DB password from BASH script
# -----------------------------------------------------
mysqladmin -u root -p create drupal

echo
echo Configuring Drupal ...
echo

ln -s /usr/share/drupal /var/www/drupal
mysql -u root -p drupal < /var/www/drupal/database/database.mysql

echo
echo Configuring PHP ...
echo
echo Please enter your MySQL password: 
read PASSWORD
touch /etc/drupal/conf.php
echo <?php >> /etc/drupal/conf.php
echo $db_url = "mysql://root:$PASSWORD@localhost/drupal"; >> /etc/drupal/conf.php
echo
echo Do you have a Fully Qualified Domain Name (FQDN)? Y/N:
read YN
if [ $YN == Y ]; then
    echo Please enter your FQDN: 
    read FQDN
    echo $base_url = "http://$FQDN/drupal"; >> /etc/drupal/conf.php
fi
sed -e 's/;extension=mysql.so/extension=mysql.so/g' /etc/php4/apache2/php.ini
sed -e 's/;extension=gd.so/extension=gd.so/g' /etc/php4/apache2/php.ini
/etc/init.d/apache2 restart
echo
echo Installation and setup are now complete.
# -------------------------------------------------------------------------
# Get server's IP address
# echo Open a web browser to http://$IPADDRESS/drupal and begin configuring
# -------------------------------------------------------------------------
sleep 15

```

---

### Post by sto6ma9ch on 2006-08-06
I've done some testing and made some modifications to the script. Here's the second draft.
```
#!/bin/bash

# Add multiverse repositories to /etc/apt/sources.list

echo
echo Setting up sources.list file ...
echo

mv /etc/apt/sources.list /etc/apt/sources.list.bak
touch /etc/apt/sources.list
echo ## Add comments (##) in front of any line to remove it from being checked. >> /etc/apt/sources.list
echo ## Use the following sources.list at your own risk. >> /etc/apt/sources.list
echo deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse >> /etc/apt/sources.list
echo ## MAJOR BUG FIX UPDATES produced after the final release >> /etc/apt/sources.list
echo deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse >> /etc/apt/sources.list
echo ## UBUNTU SECURITY UPDATES >> /etc/apt/sources.list
echo deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse >> /etc/apt/sources.list
echo deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse >> /etc/apt/sources.list

# Update apt package cache

echo
echo Updating apt ...
echo

apt-get update

# Install required servers/software

echo
echo Installing required services and software ...
echo

apt-get install apache2 libapache2-mod-php4 mysql-server drupal -y --force-yes -qq

# Configure services

echo
echo Configuring Apache2 ...
echo

sed 's/#AddType application\/x-httpd-php .php/AddType application\/x-httpd-php .php .phtml/g' /etc/apache2/apache2.conf > apache2.conf.new
mv /etc/apache2/apache2.conf /etc/apache2/apache2.conf.bak
mv apache2.conf.new /etc/apache2/apache2.conf

echo
echo Configuring MySQL ...
echo

echo -e "Please enter the password that you'd like to use for MySQL: \c"
read PASSWORD
mysqladmin -u root password $PASSWORD
echo The rest of this script's password prompts will be asking for your MySQL password.
mysqladmin -u root -p create drupal

echo
echo Configuring Drupal ...
echo

ln -s /usr/share/drupal /var/www/drupal
mysql -u root -p drupal < /var/www/drupal/database/database.mysql

echo
echo Configuring PHP ...
echo

touch /etc/drupal/conf.php
echo "<?php" >> /etc/drupal/conf.php
echo -e "\$db_url = \"mysql://root:$PASSWORD@localhost/drupal\";" >> /etc/drupal/conf.php
echo
echo -e "Do you have a Fully Qualified Domain Name (FQDN)? Y/N: \c"
read YN
if [ $YN = "Y" ]
then
    echo -e "Please enter your FQDN: \c"
    read FQDN
    echo -e "\$base_url = \"http://$FQDN/drupal\";" >> /etc/drupal/conf.php
fi
echo -e "?>" >> /etc/drupal/conf.php
cp /etc/php4/apache2/php.ini /etc/php4/apache2/php-ini.bak
sed -e 's/;extension=mysql.so/extension=mysql.so/g' 's/;extension=gd.so/extension=gd.so/g' /etc/php4/apache2/php.ini.bak >> /etc/php4/apache2/php.ini
/etc/init.d/apache2 restart
echo
echo Installation and setup are now complete.
# -------------------------------------------------------------------------
# Get server's IP address
# echo Open a web browser to http://$IPADDRESS/drupal and begin configuring
# -------------------------------------------------------------------------
sleep 15

```
There are a few issues that I'd like to clear up. 
[LIST]
[*]The script pauses for a long time right as all of the packages are about to be installed
[*]The conditional expression doesn't work as expected; it waits continually; the script never completes
[*]I'd like the last line echoed to inform the user of the exact URL to use, but I'm not sure how to get a line that just contains the IP address of the current box
[/LIST]
If anyone can help squash those bugs, it would be greatly appreciated.

---

### Post by stewski on 2006-08-11
I'm currently playing with this
[http://www.modxcms.com/](http://www.modxcms.com/)

its a little bit techie but the html/css template system is more WCAG accessibility friendly than the other CMS I looked at.
you can rewrite URLs to be search engine friendly and the community is a growing bunch of knowledgable/nice peeps, just like ubuntuforums :-)

I've heard it described as a fork of etomite though I'm not sure the devs would agree...

---

### Post by oliwally on 2006-09-01
> Now we need to create a new database for Drupal. In this example we'll name the database "drupal".
Code:

```
mysqladmin -u root -p create drupal
```

I'm getting the following error when I do that:

```
mysqladmin -u root -p create drupal
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
```
I entered my root password, and this keeps on happening. What am I doing wrong?

---

### Post by brittan on 2006-09-01
Just wanted you to know your work is appreciated...worked for me the first time...and I am new to Linux and Drupal.
Thanks...

---

### Post by netTR on 2006-09-01
Why ?

```
nettr-desktop:~$ sudo apt-get install drupal
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package drupal
```

---

### Post by denday on 2006-09-02
check your /etc/apt/source.list

and uncomment all repro. that will help :D

---

### Post by denday on 2006-09-02
Now I got this error message :

```
warning: session_regenerate_id() [function.session-regenerate-id]: Cannot send session cookie - headers already sent by (output started at /usr/share/drupal/themes/engines/xtemplate/xtemplate.inc:42) in /usr/share/drupal/modules/user.module on line 797.

warning: Cannot modify header information - headers already sent by (output started at /usr/share/drupal/themes/engines/xtemplate/xtemplate.inc:42) in /usr/share/drupal/includes/common.inc on line 159.
```

---

### Post by sto6ma9ch on 2006-09-06
> **oliwally said:**
> I'm getting the following error when I do that:

```
mysqladmin -u root -p create drupal
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
```
I entered my root password, and this keeps on happening. What am I doing wrong?

Were you successful in setting the root MySQL password? It would have been this part of the HOWTO:
```
mysql> UPDATE mysql.user SET Password=PASSWORD('your_new_password')
WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> quit
```

---

### Post by sto6ma9ch on 2006-09-06
> **denday said:**
> Now I got this error message :

```
warning: session_regenerate_id() [function.session-regenerate-id]: Cannot send session cookie - headers already sent by (output started at /usr/share/drupal/themes/engines/xtemplate/xtemplate.inc:42) in /usr/share/drupal/modules/user.module on line 797.

warning: Cannot modify header information - headers already sent by (output started at /usr/share/drupal/themes/engines/xtemplate/xtemplate.inc:42) in /usr/share/drupal/includes/common.inc on line 159.
```

You may need to go back over some of the database setup steps to see if you left anything out. Also check your /etc/drupal/conf.php and /etc/php4/apache2/php.ini files to ensure that 1.) they exist and 2.) they contain the correct information. If you run into any questions or if that doesn't help, please let us know.

---

### Post by tigerinamerica on 2006-10-02
I have one problem with Ubuntu and Drupal, which is taking my nights and nights...

I have domain registrationg with GoDaddy.com
I am using Dynamic IP address so I used No-ip.com account.
so my current setup is like...

GoDaddy holds [www.tigerinamerica.com](www.tigerinamerica.com) registration
No-ip.com holds tiger.no-ip.com registration and it knows my Dynamic IP Address for server running at home.


GoDaddy.com ( [www.tigerinamerica.com](www.tigerinamerica.com)) points to [http://tiger.no-ip.com:5555/drupal](http://tiger.no-ip.com:5555/drupal)

and No-IP.com forwards it to my router and Webserver which is running at home.

In GoDaddy option, I hav used Mask Option...

Problem is when someone try to visit [www.tigerinamerica.com](www.tigerinamerica.com) forwarding works ok and visitor can see my Drupal site. Address bar is also saying [www.tigerinamerica.com](www.tigerinamerica.com) but in all the pages if I place my mouse pointer on the link, all the link ref. reads at [http://tiger.no-ip.com:5555/drupal](http://tiger.no-ip.com:5555/drupal) instead of [www.tigerinamerica.com](www.tigerinamerica.com)

Due to this user can not login because cookie is created for tiger.no-ip.com and it needs to be for [www.tigerinamerica.com](www.tigerinamerica.com)

I tried Apatche's URL Rewriting, but it does not resolves the links generated inside the page page.

My HTTP_HOST variables value holds tiger.no-ip.com:5555 which needs to be hold [www.tigerinamerica.com](www.tigerinamerica.com)

Is there way, I can update HTTP_HOST variable for Drupal site?

I tried to set $base_url in settings.php file for Drupal but it didn't resolve problem.

Any clue or help will be appriciated.

Thanks in Advance.

---

### Post by az on 2006-10-02
I don't think running using the mysql root account is very smart.

Also, you can use the packages from main to run drupal on the supported LAMP stack (without universe).

[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by DigitalDuality on 2006-10-21
edit

---

### Post by DigitalDuality on 2006-10-21
edit

---

### Post by DigitalDuality on 2006-10-21
d

---

### Post by DigitalDuality on 2006-10-23
d

---

### Post by Linux O)o_O7 on 2006-11-04
Can I use synaptic to install PHP and apache before I use this Drupal install guide? I mean I already have, so will it work for me when using this guide?

---

### Post by az on 2006-11-04
> **Linux O)o_O7 said:**
> Can I use synaptic to install PHP and apache before I use this Drupal install guide? I mean I already have, so will it work for me when using this guide?

You can with this one:
[https://help.ubuntu.com/community/Drupal](https://help.ubuntu.com/community/Drupal)

---

### Post by Brockett on 2006-11-21
I am getting a error when trying to access via browser:
-------------------------------------------------------------------
Forbidden

You don't have permission to access /drupal on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 Server at 192.168.1.9 Port 80
-------------------------------------------------------------------

I followed exact install process step by step. I did the install on ubuntu server 6.10 over SSH from a box on my LAN. Also get the same error when trying to access from the WAN address that I have ported for this web server. 

Thanks for any help in advance. 

2nd month with ubuntu and have now installed on my server, laptop, and desktop. So I guess I am a newbie with passion.

Thanks again,
Brockett

---

### Post by adamkane on 2006-11-21
Following instructions exactly doesn't keep you out of trouble with CMSes like drupal. You probably have some directory with incorrect permissions.

---

### Post by Brockett on 2006-11-21
OK, I am an idiot.. here is what I had wrong.

In the  "sudo nano /etc/drupal/conf.php"

In in the second line:

<?php
_$db_url = "mysql://root:your_database_password@localhost/drupal";_
$base_url = "http://drupal_server's_ip_address/drupal";
?>

I had:
$db_url = "mysql://root:your_database_password@127.1.1.0/drupal";

If I had been in my right mind I would have at least put "127.0.0.1" and that would have made some kinda sense. 

I replaced "127.1.1.0" with "localhost" as sto6ma9ch had posted. Then everything worked.

Man, I hope this will help with some body in the future. Other than being the dumb dumb that missed one step and screwed it all up.

Thanks,
Brockett

---

### Post by Brockett on 2006-12-14
> 
For those of you who will be adding the photo/video module to your site, uncomment this line as well (trust me, you don't want to start hunting for this one after the fact):
```
;extension=gd.so
```
... and make it look like this:
```
extension=gd.so
```
Press Ctrl+X to exit nano, type "Y" to save your changes, and press Enter to
accept the filename. We're almost finished. The next thing to do is to restart the web service, and you're ready. Do it thus-ly:



The gd library is not installed by default.  With much trial and error I found a solution for my particular problem.

sudo apt-get install php4-gd2

And now everything works fine.

Hope that helps!

---

### Post by jnoreiko on 2007-01-25
I've installed the mysql package, but when I try to set the password I get this:

```
joachim@ubuntu:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

---

### Post by az on 2007-01-25
> **jnoreiko said:**
> I've installed the mysql package, but when I try to set the password I get this:

```
joachim@ubuntu:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```
Try
mysql -u root -p

---

### Post by Sluff on 2007-02-06
I just noticed the date on your original post so Im wondering if this is even relevant.  I followed your steps and it generated no errors.  However when trying to access drupal from my web browser I get this error:

Fatal error: Call to undefined function: mysql_connect() in /usr/share/drupal/includes/database.mysql.inc on line 31

I tried installing this previously to finding your howto so who knows what went wrong.  I kept getting version errors.  Drupal 5.1 wanted a mysql 3.x or 4.0 database.  I removed it all and tried your howto.  Any suggestions?  Thanks...

Sluff.

---

### Post by jnoreiko on 2007-02-10
> **az said:**
> Try
mysql -u root -p

I get the same thing I'm afraid:

```
joachim@ubuntu:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

I've tried doing this with sudo as well -- same result.
I don't get it. How is mysql meant to be used if I can't even start it from a fresh installation?

---

### Post by jrobinson5 on 2007-02-25
OK, I'm installing this on a Hoary server, and I'm using a different http directory than normal, so I'm refactoring the commands as needed.

> **sto6ma9ch said:**
> For this next step, we're going to set up the "drupal" database scheme. Normally this would be a very tedious process. Fortunately, Drupal comes with a script to help automate this. Instead of manually creating the schema, just type in this command:
```
mysql -u root -p drupal < /var/www/drupal/database/database.mysql
```


This is the part that trips me up. I get the following error:

```
jrobinson@wwwserver:~/public_html/drupal$ sudo mysql -u root -p drupal < /home/jrobinson/public_html/drupal/database/database.mysql
Enter password:
ERROR 1049: Unknown database 'drupal'
```

What gives?

James

---

### Post by sto6ma9ch on 2007-02-26
What happens when you run this command?
```
mysqladmin -u root -p create drupal
```

---

### Post by jnoreiko on 2007-02-26
I fixed the mysql problem, but I have no idea how -- I tried a sequence of commands, each of which gave similar errors, and then the original command worked.

As for creating the drupal database, try installing phpmyadmin. Straight from installing you can get to it at localhost/phpmyadmin and set up the database and users through browser pages.

---

### Post by jrobinson5 on 2007-02-26
OK, I must have skipped that direction by accident. Anyway it seemingly worked fine after that, but when I tried to access it, I get a 500 Internal Server Error.

Here's the page:
[http://crfo.ath.cx/drupal](http://crfo.ath.cx/drupal)

And here's Apache's error log:
[http://crfo.ath.cx/error.log](http://crfo.ath.cx/error.log)

What gives?

James

---

### Post by garyalldredge on 2009-08-26
> **netTR said:**
> Why ?

```
nettr-desktop:~$ sudo apt-get install drupal
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package drupal
```
You should do this instead

apt-get install drupal6

that will solve the issue

---

### Post by garyalldredge on 2009-08-26
Well i am here to see if someone can help automate this script.  

Here it is

CODE

```

#!/bin/sh
sudo apt-get install linux-headers-`uname -r` build-essential &&
mount /dev/cdrom &&
cp /media/cdrom/VMwareTools-*.tar.gz /tmp/ &&
cd /tmp/ &&
tar xf VMwareTools-*.tar.gz &&
cd vmware-tools-distrib/ &&
sudo ./vmware-install.pl –default &&
apt-get install apache2 &&
sudo /etc/init.d/apache2 restart &&
sudo apt-get install php5 libapache2-mod-php5 &&
sudo /etc/init.d/apache2 restart &&
sudo nano /var/www/test.php &&
sudo /etc/init.d/apache2 restart &&
sudo apt-get install mysql-server &&
sudo apt-get install libapache2-mod-auth-mysql php5-mysql phpmyadmin &&
sudo /etc/init.d/apache2 restart &&
sudo apt-get install php5-mysql mysql-client &&
sudo /etc/init.d/apache2 restart &&
sudo apt-get install drupal6 &&
nano /etc/samba/smb.conf  &&
/etc/init.d/samba restart &&
nano /etc/php5/apache2/php.ini &&
/etc/init.d/apache2 restart &&
/etc/init.d/samba restart &&
sudo apt-get update &&
sudo apt-get install build-essential subversion git-core checkinstall yasm texi2html libfaac-dev libfaad-dev libmp3lame-dev libsdl1.2-dev libtheora-dev libx11-dev libxvidcore4-dev zlib1g-dev &&
cd / &&
git clone git://git.videolan.org/x264.git &&
cd x264 &&
./configure &&
make &&
sudo checkinstall --fstrans=no --install=yes --pkgname=x264 --pkgversion "1:0.svn`date +%Y%m%d`-0.0ubuntu1" --default &&
cd / &&
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg &&
cd ffmpeg &&
./configure --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab &&
make &&
sudo checkinstall --fstrans=no --install=yes --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --default &&
end
```

---

### Post by tomthumb99 on 2009-10-27
Folks,

My Drupal6, MySQL and Tomcat are working, thanks to this post and the related official ubuntu-drupal directions.

Next, how to a install the sub-drupal packages (cpannel, nodewords..)without screwing up the working setup.  Can somebody kindly list the steps.  I can un-zip the tar files and see the new folders/files just fine, but where to copy them? How does Drupal know the new sub-packages are inplace.  Also, the chmode command for correct file ownership.

Thanks,

TH

---

### Post by ihatethetv on 2010-02-09
I'm with tom thumb.  Those would be good instructions.

Also any information on how to update drupal?  I just installed via instructions above and it's out of date out of the box.

---

