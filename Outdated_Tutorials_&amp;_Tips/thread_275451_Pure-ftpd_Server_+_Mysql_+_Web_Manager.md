---
title: "Pure-ftpd Server + Mysql + Web Manager"
date: 2006-10-11
forum: Outdated Tutorials &amp; Tips
---

### Post by XplOzIOn on 2006-10-11
[B]This is my first tutorial :D

Pure-ftpd [COLOR=Red]XplOzIve[/COLOR] Tutorial [COLOR=Blue]v1[/COLOR][/B] by [COLOR=DarkRed]xplozion[/COLOR]

Before we start installing this lets make sure we have the next packages installed: copy & paste in terminal

```
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get -y install apache2 php5 libapache2-mod-php5 mysql-server libapache2-mod-auth-mysql libapache2-mod-auth-mysql php5-mysql build-essential phpmyadmin libmysqlclient15off openssl libssl-dev
sudo apt-get install libmysqlclient15-dev
```

Setting up mysql password:
```
mysqladmin -u root password [COLOR="Red"]YourPasswordHere[/COLOR]
```

Now logged as the user you want to run the server go to its home and download the packages we need. Lets start with pure-ftpd
```
wget ftp://ftp.pureftpd.org/pub/pure-ftpd/releases/pure-ftpd-1.0.21.tar.gz
```

After downloading lets untar it (Note that im using latest release when this tutorial was made)
```
tar -xvvzf pure-ftpd-1.0.21.tar.gz
```

With the folder there lets change its name
```
mv pure-ftpd-1.0.21/ pure-ftpd
now go into the folder 'cd pure-ftp/'
```

Time to configure and compile
```
./configure --with-everything --with-paranoidmsg --with-virtualchroot --with-tls --with-largefile --with-mysql
make
make install
```

If theres a error here if because some missed packages, just install it via 'sudo apt-get -y install package name'

Now its time to download our Web manager (**Machiel's  User manager for PureFTPd**)
```
cd ..
wget http://machiel.generaal.net/files/pureftpd/ftp_v2.1.tar.gz
tar -xvvzf pureftpd/ftp_v2.1.tar.gz

```

Once we have the it, we need move our new 'ftp' folder to wwwroot path (Note this path changes if your default www root folder is different)
```
mv ftp/ /var/www/
sudo chown www-data /var/www/ftp -R
```

Now we need to configure our new pure-ftpd web manager and for that we go to [http://localhost/ftp/install.php]("http://localhost/ftp/install.php")

This web based pure-ftpd manager its pretty simple to follow and i think you wont be having any problems ;)
Now remember to copy and paste the file for pureftpd-mysql.conf (The content of this file is given by the manager)

**Options for pure-ftpd server:**
There are many ways and differents styles and settings. You can check all the options here [http://jeanmatthieu.free.fr/pureftpd/doc/adv/man/pure-ftpd.html]("http://jeanmatthieu.free.fr/pureftpd/doc/adv/man/pure-ftpd.html")

**Starting our pure-ftpd server**
Now will all done lets start our pure-ftpd server:
```
pure-ftpd -l mysql:/home/myuser/pure-ftpd/pureftpd-mysql.conf &
```
This way it will run in the backgroud. Have fun :D


[COLOR="Red"]******* IMPROVEMENTS *******[/COLOR]
This are things that id like to add to this tutorial but since i am not a linux expert cant really tell how to do it:

1. Stating pure-ftpd when linux starts.
2. Web stats for FTP transfer (Adding it to this tutorial in a few).


[COLOR="Red"]******* KNOW ISSUES *******[/COLOR]

1. For some reason it wont let me login using SSL. But TLS does work.
2. Using the FXP protocol gives me real slow speed(100kb/s)

---

### Post by XplOzIOn on 2007-02-21
Ill redo this tutorial, with latest test and some plus..

Any Comments anyone?

---

### Post by crosswing on 2007-02-27
Checking connection to MySQL server 	Failed why it said like that ? help

---

### Post by XplOzIOn on 2007-03-15
There could be several reason for this. I mave seen that when you change the password and DB sometimes it gives you an error. I tend to leave it defaults and make phpmyadmin only accesible from local network.

So try using defaults for pure DB

---

