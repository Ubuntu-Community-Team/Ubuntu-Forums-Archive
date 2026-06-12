---
title: "Running SQL from the command line with XAMPP install"
date: 2010-01-25
forum: Programming Talk
---

### Post by LumbeeNDN on 2010-01-25
Just wondering if anyone has any thoughts on this. I'm doing some SQL work so I did an XAMPP install on Ubuntu 9.10. SQL ran OK, but I had to use phpMyAdmin for administration of the DB. I was not able to run "mysql" from the command line. I did uninstall XAMPP and separate apt-get installs of apache/PHP/mysql, and now I can do all the command line stuff. Any ideas on why I could not run the mysql from the command line with the XAMPP install?

---

### Post by Can+~ on 2010-01-25
```
sudo apt-get install mysql-client
```

In fact, you can install a LAMP from the command line:

```
sudo apt-get install mysql apache2 libapache2-mod-php5
```

(or libapache2-mod-[whatever you want])

Also, to administer a MySQL database with local GUI-based applications (instead of phpMyAdmin), also install:

```
sudo apt-get install mysql-query-browser mysql-admin
```

---

### Post by LumbeeNDN on 2010-01-25
...good response Can...so let me make sure I have the this straight. If I just do the normal XAMPP install, I don't have the mysql client? ...and "sudo apt-get install mysql-client" gives me  the command line client?

---

### Post by Can+~ on 2010-01-25
> **LumbeeNDN said:**
> ...good response Can...so let me make sure I have the this straight. If I just do the normal XAMPP install, I don't have the mysql client? ...and "sudo apt-get install mysql-client" gives me  the command line client?

Where did you get the XAMPP Client? Did you downloaded it as a separate pacakage, or is it available in the repository?

I suspected that because you're new here, that you probably come from windows, and have the impression that everything must be installed from separate.

Debian (and therefore, ubuntu) has a connection with a server called "the repository" where you can download OSS software and some restricted things. It's preferable to install things from this place instead of you downloading and/or compiling them manually (although, .debs are fine). The reason is that, that way, the package manager can keep track of where things are installed, and offer tools to remove them (sudo apt-get remove/purge <package name>), upgrade them (apt-get upgrade) and other things (solve dependencies, offer suggested packages and documentation).

The commands I gave you are just invocations to the repository through command line, you can get also with the GUI application "Ubuntu Software Center" in the "Applications" menu, and the more advanced, developer-friendly GUI in "System > Administration > Synaptic Package Manager".

---

### Post by jeffathehutt on 2010-01-25
If you did download and extract the .tar file yourself, chances are that the mysql server is not set to use the default location for its .sock file.  So, the client doesn't know where to connect.  On my system, the .sock file is located at /opt/lampp/var/mysql/mysql.sock, rather than the default /var/run/mysqld/mysqld.sock

So, if you want to use the mysql client with xampp, you would need to run the command
```
mysql -S /opt/lampp/var/mysql/mysql.sock
```
and it should be able to connect.  If you extracted the .tar file in some other location, you will have to adjust the paths. :)

---

### Post by LumbeeNDN on 2010-01-25
> **Can+~ said:**
> Where did you get the XAMPP Client? Did you downloaded it as a separate pacakage, or is it available in the repository?

..I'm pretty sure I download the tar from the XAMPP web site, and exploded it myself. 

...yes, I am a total nube, but have been using Ubuntu almost exclusively for the last month now with only an occasional use of XP, so I'm almost fully weaned! 

...good tip on just using the repository for installs. That makes sense that the system can keep track of what is/is not installed if you install from there. I'll keep that in mind for future reference...thanx...

---

### Post by LumbeeNDN on 2010-01-25
> **jeffathehutt said:**
> If you did download and extract the .tar file yourself, chances are that the mysql server is not set to use the default location for its .sock file.  So, the client doesn't know where to connect.  On my system, the .sock file is located at /opt/lampp/var/mysql/mysql.sock, rather than the default /var/run/mysqld/mysqld.sock

So, if you want to use the mysql client with xampp, you would need to run the command
```
mysql -S /opt/lampp/var/mysql/mysql.sock
```and it should be able to connect.  If you extracted the .tar file in some other location, you will have to adjust the paths. :)

...well there ya go...that was probably my problem!!! :rolleyes:

---

### Post by Hellkeepa on 2010-01-25
HELLo!

Trust me, and **Can+~**, when we tell you to forget about the XAMPP package. Remove it completely, and follow **Can+~**'s instructions in the second post of this forum. Then you'll have everything you need, all installed and configured for you. You'll also be notified about any updates to any of the software you've installed via the package manager, which are installed in a one-click process via the pacakge manager. In contrast to packages you download from the net, which you'll have to monitor the web page yourself, and download & install the upgrades manually.

Happy codin'!

---

