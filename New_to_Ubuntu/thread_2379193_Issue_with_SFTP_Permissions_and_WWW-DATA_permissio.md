---
title: "Issue with SFTP Permissions and WWW-DATA permissions"
date: 2017-12-02
forum: New to Ubuntu
---

### Post by waslsdnowlds on 2017-12-02
I cannot for the life of me get my permissions to stick with newly uploaded sftp files to give rights to the www-data user to delete them via php. This needs to occur for an installation in a PHP software package I developed. It works great on any bluehost.com server. So, starting to get back into Ubuntu, I installed Ubuntu w/ AWS (free server) and did the following below to set up the Apache2 server w/ PHP 7.0.


```

//ssh
ssh -i mysite.pem ubuntu@99.99.99.99


//always sudo
exec sudo -i


//update apt-get
apt-get update


//setup apache2
apt-get install apache2


//setup php7.0
apt-get install php7.0 php7.0-fpm php7.0-mysql
apt-get install libapache2-mod-php7.0


//setup mysql
apt-get install mysql-server
mysql_secure_installation


//create mysql user-log into mysql
mysql -u root -p
mysql -p


//create mysql database
create database <name>


//exit mysql
exit


//setup svsftpd
sudo apt-get install vsftpd


//restart services
service apache2 restart

```


sftp is done via the ubuntu user.
Test sftp with some sample code in var/www/html and it works fine when tested in browser.
I then place installation package in the var/www/html directory.
Via web browser, I install the software. Last part needs to create a config.php file delete files in the var/www/html/install directory, and delete var/www/html/install directory. All done via the www-data user. This obviously doesn't let me do either one of those tasks.


I then do the following below to modify the var/www/html directory to have the www-data and ubuntu users to have total freedom with permissions. I want to have the permissions created by the website group, on all files and directories inside of var/www/html, to be -rwxrwxr-x and drwxrwxr-x.


```

//create group
groupadd -g 2710 website


//add users to group
usermod -g website www-data
usermod -g website ubuntu
usermod -g website root


//change directory group
chgrp website var
chgrp website var/www
chgrp website var/www/html


//set directory permissions
chmod 775 var
chmod 775 var/www
chmod 775 var/www/html


//set setgid
chmod g+s var
chmod g+s var/www
chmod g+s var/www/html


//set default permissions for group
setfacl -dm g::rwX var
setfacl -dm g::rwX var/www
setfacl -dm g::rwX var/www/html


Set Default Permissions for Others
setfacl -dm o::0 var
setfacl -dm o::0 var/www
setfacl -dm o::0 var/www/html

```


Currently, I get the following below when I SFTP with the ubuntu user when it comes to permissions.


Files get -rw-rw-rw-. ubuntu/website
Directories get drwxrwsrwx. ubuntu/website


Anyone out there could clue me in with my first or many mistakes please? :)

---

