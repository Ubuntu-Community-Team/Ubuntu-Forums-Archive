---
title: "HOWTO: Quick-n-easy LAMP for Newbies"
date: 2005-03-03
forum: Outdated Tutorials &amp; Tips
---

### Post by machiner on 2005-03-03
A quick and painless LAMP install/config for Ubuntu.

I don't run Apache2 so this howto will focus on Apache 1.3. As well, I think Webmin makes setting LAMP up very easy, even though we don't really use it for much.  So this howto will include those instructions as well.

Considering the proliferation of Content Managers like Mambo and Drupal (et al) we will also make changes to allow for these scripts to run locally without impediment.
***********************
For Hoary users:
Open up your Synaptic and install the following:

ssleanet (sp) OPTIONAL
apache
apache-common
apache-utils
libapache-mod-perl
libapache-mod-php4
libapache-mod-ssl
*********
mysql-client
mysql-common
mysql-server
libmysqlclient12
libqt3c102-mt-mysql
libdbd-mysql-perl
php4-mysql
*********
php4
php4-pear
php4-imagick
php4-common
php4-gd2
*******************
Some of the applications already come pre-installed with Ubuntu, and some will include dependancies. As well, you may not want to install php4-imagick, or php4-gd2, but you will find that some scripts (SugarCRM) will want these and others.

For Warty users I found it necessary to add a Debian repository in order to install libapache-mod-php4. At the command prompt type:
sudo gedit /etc/apt/sources.list

add this line:
deb [ftp://ftp.debian.org/debian](ftp://ftp.debian.org/debian) sarge main contrib non-free #

You must then type: sudo apt-get update
 Or, you may just save the file, and open synaptic and update it there. Don't forget to comment out this line or remove it once you have installed the necessary php4 lib.

*******************

To make things a little easier we work with Webmin. Goto: 
[http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz](http://prdownloads.sourceforge.net/webadmin/webmin-1.180.tar.gz)
and pick your mirror.  Once downloaded, extract webmin into a directory of your choice and open a terminal. Goto the extracted webmin directory land type the following:

sudo sh setup.sh /usr/local/webmin

From there follow the prompts, mostly just enter. You may choose your port, uname and password. You may also decide to run Webmin securely - always a good idea. You must have SSLeanet (SP) installed. It's in the repository, or - you can install it when you are in Webmin. As well, you may choose to have Webmin start at boot or no. I choose no. The command to start Webmin when you need it is the following:

sudo /etc/webmin/start   to stop it when your finished:  sudo /etc/webmin/stop

Everything installed? Good. Close everything. Shake it off.

***********************************

Open a terminal and type the following command as a regular user:
mysqladmin -u root password <password> (pick a password)

Now start Webmin. You can leave the terminal open.  Open your browser and point to: 127.0.0.1:10000   Of course, if you changed the port at installation you would choose that port instead of 10000. As well, if you had ssleanet installed already and webmin installed allowing secure browsing, you would point to this address:
[https://127.0.0.1:10000](https://127.0.0.1:10000)

*********************************

Navigate to the SERVERS aspect of Webmin. You will see Apache and 2 below it you will see MySQL. Click on Apache.  The first screen you see will "confirm" your modules. You should see "php4" and a few others.  Choose OK. If you don't see what you want, it might be installed with Apache anyway. This howto is limited.  Next screen you will see your Apache modules, at the top of your screen you will see commands to Apply Changes, Stop/Start Apache, etc. Stop Apache.

You will see an icon for "edit config files" Click that.  There are 4 or 5 things to change. I only change enough to run Mambo sites, and cgi scripts locally. I'm no Apache expert.

Scroll down in the config file until you come to this section:

# First, we configure the "default" to be a very restrictive set of 
# permissions.  
#
<Directory />
    Options SymLinksIfOwnerMatch
    AllowOverride None      <<<<<<<<<<change None to read: All
</Directory>


Goto this section next:
# This controls which options the .htaccess files in directories can
# override. Can also be "All", or any combination of "Options", "FileInfo", 
# "AuthConfig", and "Limit"
#
    AllowOverride None <<<<<<<<<<<<<<change None to All

next:

<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.htm index.shtml index.cgi
</IfModule>

Make sure that "index.php" is FIRST in the above line.

Next, if you want to run cgi-bin locally and you have your cgi-bin in your /var/www directory change the following to reflect that:

<IfModule mod_alias.c>
    ScriptAlias /cgi-bin/ /var/www/cgi-bin/   <<<<<<<<<<<<<<<<<<<<<<<<<<<

#
# "/usr/lib/cgi-bin" could be changed to whatever your ScriptAliased
# CGI directory exists, if you have that configured.
#
    <Directory /var/www/cgi-bin/>  <<<<<<<<<<<<<<<<<<<<<<<<<
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
</IfModule>

I think the default local for cgi-bin is : var/lib/cgi-bin  or something like that. 

Next goto the following section:

    # And for PHP 4.x, use:
    #
    #AddType application/x-httpd-php .php  <<<<<<<<<<<<<<<<<<<uncomment
    #AddType application/x-httpd-php-source .phps <<<<<<<<<<<<uncomment

That's all I ever do to change my config file. Click the SAVE button.

*********************

Next, you need to change php.ini to alloy running the mysql add-on. Alt-Tab to your terminal, start another session and type the following:
sudo gedit /etc/php4/apache/php.ini

ctrl+F to find : mysql.so   it will be in the Dynamic Extensions area. Looks like this:
; Example lines:

;extension=mysql.so
;extension=gd.so
;extension=udb.so

remove the semi-colon for mysql.so. Scripts like SugarCRM need to run the GD Graphics library that's why we installed the module originally and you can uncomment it now in your php.ini file. Save the file, close it.

*******************************

Alt-Tab back to Webmin. You may now Start Apache.  Click on the Servers icon in Webmin, click on MySQL.  You should be greeted with a uname/passwd login screen. Your password that you chose earlier is already in the field as stars. You may click login.  Now you may Start MySQL.

****************

You are finished. You may close everything out, run the STOP comand for Webmin and populate your /var/www folder with all your fancy websites and and cgi-scripts.

Typical Disclaimer:
I hope this solves many of the problems that crop up on the forum frequently.
You machine is different than mine. YMMV - I do this exact setup every time on my machine and others with good results.  If you want to run Apache2, more power to you but I could never figure out how to allow the modrewrite to work in Apache2 - this means that I couldn't setup Mambo for using "nice" URLS.  You may be able to do that -- Rock On.

---

### Post by NiceGuyUK on 2005-08-23
Very good guide - got me up and running nice and quickly.  Added PHPMyAdmin to my setup and that worked too, although it got confused on install because of using Apache instead of Apache2.

All in all, great work Machiner!  :grin:

---

### Post by toppy on 2005-12-29
Thanks for your guide Machiner, I was up and running Apache 1.3/Mysql 4.1 on Breezy Badger with very little complications!  

Just a couple of notes for others that my install seemed to differ on.

1) For Breezy Badger repository, I changed my sources.list as shown at: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php) (thanks to Matthews post: [http://ubuntuforums.org/showthread.php?t=106703&highlight=breezy+badger+repository](http://ubuntuforums.org/showthread.php?t=106703&highlight=breezy+badger+repository))

2) The GD2 package on Breezy Badger was actually listed as "php4-gd".

3) I went for mysql 4.1 so packages were:
mysql-client-4.1
mysql-common-4.1
mysql-server-4.1

4) Webmin didn't seem to do much for me so I just modified config files from shell.  Possibly this is why I had a little bit of a problem.  PHP wasn't working at first so aside from the configuration changes you wrote I had to add "LoadModule php4_module /usr/lib/apache/1.3/libphp4.so" to Apache's module.conf.

That was it.  Thanks again for the guide Machiner.

---

