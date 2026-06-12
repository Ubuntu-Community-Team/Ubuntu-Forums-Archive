---
title: "HOWTO: Install Relay AJAX File Server on Ubuntu 6.06 LTS LAMP Server"
date: 2006-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by crichell on 2006-07-12
Relay is an awesome **free** and **open source** web based AJAX file storage and serving application. This article describes how to install Relay on Ubuntu 6.06 LTS. This installation is completed on a fresh Ubuntu 6.06 LTS LAMP Server installation.

The original How To is [here.]("http://knowledge76.com/index.php/Relay_AJAX_File_Server_on_Ubuntu_6.06_LTS_%28Dapper_Drake%29")

Check out Relay [here.]("http://ecosmear.com/relay/")

Most commands can be cut and pasted into your terminal - adjust for your own passwords. One command per line. So lets get started.

**Install Ubuntu Lamp Server**
[LIST=1]
[*]Download and burn the Ubunty 6.06 LTS Server CD
[*]Boot from the CD and choose Install LAMP Server
[*]Get your server up to date:
[/LIST]
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo reboot
```

**Install Dependencies**

We will now install ImageMagick, GD2, and GhostScript. These applications are used for creating nice thumbnails of the files on your server.

```
sudo apt-get install php5-gd imagemagick gs-common unzip libapache2-mod-perl2
sudo /etc/init.d/apache2 force-reload
```

**Setup MySQL**

To setup MySQL you will need to first create a password for your mysql root user. After that we create your Relay database and a new MySQL user with access to the Relay database. Record the following information. Adjust with your own passwords, database name, Relay admin username.

MySQL Root Password: mysqlrootpw
Relay Database Name: relay
Relay Database Table Prefix: relay_
Relay Database Username: relaydbuser
Relay Database Password: relaydbpass

Relay Admin Username: admin
Relay Admin Password: relayadminpass

**Create MySQL Root Password**

The following commands create your MySQL root password.
```
sudo mysqladmin -u root password mysqlrootpw
```
For the next command you will be prompted for a password. Enter the mysqlrootpw you just created.
```
sudo mysqladmin -u root -p -h localhost password mysqlrootpw
```

**Create Relay Database and Database User**

The following commands will create our Relay database and the database user. When prompted for a password enter your mysqlrootpw.
```
mysql -u root -p
create database relay;
grant all privileges on relay.* to 'relaydbuser'@'localhost' identified by 'relaydbpass';
exit
```

**Download Relay**

Now we need to download Relay and place it in the appropriate directory.

```
wget http://ecosmear.com/relay/download.php?download=true
sudo unzip relayb01-070606.zip
sudo cp -r relay /var/www/
```

**Configure Permissions**

Next we'll set the appropriate permissions.

```
cd /var/www/

sudo chown www-data relay/
sudo chown www-data relay/uploads/
sudo chown www-data relay/filestore/
sudo chown www-data relay/upload.pl
sudo chmod 755 relay/
sudo chmod 755 relay/upload.pl
sudo chmod 755 relay/uploads/
sudo chmod 755 relay/filestore/
```

**Apache2 Config**

Next we'll edit the apache configuration file to allow CGI Perl execution in the /var/www/relay directory.

```
sudo nano /etc/apache2/apache2.conf
```
Use the down arrow key to reach the bottom of the file. Cut and paste the following lines into your terminal (at the bottom of the file).
```
<Directory "/var/www/relay/">
     AllowOverride All
     Options +ExecCGI
     AddHandler cgi-script cgi pl
</Directory>
```
Now to save the changes:
```
press Ctrl+x then y then Enter
```
Reload Apache
```
sudo /etc/init.d/apache2 force-reload
```

**Install and Configure Relay**

From another computer use Firefox (not IE only because it sucks) to browse to your relay server.
Enter the appropriate information that we recorded from above. i.e. database name, username, relay admin & password, etc.

For the **Utilities** section:
```
GhostScript: /usr/bin/gs
ImageMagick: /usr/bin/convert
```
Click **Submit Query**

**Use Relay and Have Fun**

Now browse to your new relay server. Enter the admin username and password we created earlier. Tada, woop, and whatever else - you're done. Take a look around - Relay is pretty awesome. Click Admin Panel to create new virtual directories, users, and to view statistics.

---

### Post by DX 00 on 2007-01-12
Thanks for the howto :)

---

### Post by oedenfield on 2007-11-20
I'm having permission issues using Relay with Gutsy Gibbon (non-LAMP).  I've installed all of the components and can even log in and setup new users and everything the only issue comes up when I try to upload a new file and it just stops doing anything at all.

I really like this program and would love to have it setup on my Gutsy Desktop/server.

I have Gutsy desktop installed with Apache2 and MySQL and all of the other Relay dependencies (like Perl).

Thank you.

---

### Post by davim on 2008-04-07
do you have a similar howto to configure relay using ldap?

---

### Post by jesuspresley on 2009-05-21
Thanks a lot, that really helped. 
Also, I am interested in Active Directory OR LDAP support.

Any hints?

---

