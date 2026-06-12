---
title: "Lighttpd+MySQL+PHP5"
date: 2007-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by LookTJ on 2007-01-15
According to frodon's pm, I posted a broken link...which was domain deleted yesterday by me.

So he told me to repost a working link


[http://looktj.homelinux.org/blog/?p=6](http://looktj.homelinux.org/blog/?p=6)


dns down?

try [http://67.182.24.225/blog/?p=6](http://67.182.24.225/blog/?p=6)


> 
Add all the Ubuntu universe repo.
 1. Install MySql(Database server)
sudo apt-get install mysql-server
 Copied from ubuntuguide.org
 MySQL initially only allows connections from the localhost (127.0.0.1). We'll need to remove that restriction if you wish to make it accessible to everyone on the internet. Open the file /etc/mysql/my.cnf
 gksudo gedit /etc/mysql/my.cnf
 Find the line ***bind-address = 127.0.0.1*** and comment it out
 #bind-address           = 127.0.0.1
 MySQL comes with no root password as default. This is a huge security risk. You'll need to set one
 sudo mysqladmin -u root password your-new-password
 thanks to Mike McDaniel's Question, yes replace your-new-password with a password of your choice.
 sudo mysqladmin -h root@local-machine-name -u root -p password your-new-password
 sudo /etc/init.d/mysql restart
 ok back to writing on my own :)
 2. Install Lighttpd(Webserver)
sudo apt-get install lighttpd
 3. Install PHP5-cgi(To use PHP on sites)
sudo apt-get install php5-cgi
 4. Edit fastCGI for lighttpd
 Backup the orginal fastcgi file
 sudo cp /etc/lighttpd/conf-available/10-fastcgi.conf /etc/lighttpd/conf-available/10-fastcgi.conf_backup
 Then edit the fastcgi file
 sudo gedit /etc/lighttpd/conf-available/10-fastcgi.conf
 Then replace everything with
  server.modules += ( "mod_fastcgi" )
fastcgi.server = ( ".php" =>
( "localhost" =>
( "socket" => "/tmp/php5-fcgi.socket",
"bin-path" => "/usr/bin/php5-cgi"
)
)
)

 4.1 Enable fastCGI
 sudo lighty-enable-mod fastcgi
 Then reload Lighttpd
sudo /etc/init.d/lighttpd force-reload
 5. Install php5-mysql module(to use php when connected to a database)
sudo apt-get install php5-mysql
 6. Install phpmyadmin(MySQL web interface)
sudo apt-get install phpmyadmin
 Optional:
 1. Install proftpd and gproftpd(optional)
for proftpd(FTP Server):
 sudo apt-get install proftpd
 for gproftpd(graphical interface for proftpd)
 sudo apt-get install gproftpd
 To start up gproftpd:
 sudo gproftpd
 Thank you and comment me on this guide made by me
 -Taylor from [http://ubuntuforums.org](http://ubuntuforums.org) 
 

---

### Post by LookTJ on 2007-01-20
am i allowed to bump in this board?

---

### Post by Disstress on 2007-01-21
Neither one of the links is working for me. They both time out.

---

### Post by LookTJ on 2007-01-26
> **Disstress said:**
> Neither one of the links is working for me. They both time out.
I'll make a backup link when I get on Ubuntu, I'm dual booting XP SP2 Pro right now

---

