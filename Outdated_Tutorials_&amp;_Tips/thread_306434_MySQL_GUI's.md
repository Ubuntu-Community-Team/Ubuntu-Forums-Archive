---
title: "MySQL GUI's"
date: 2006-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by DoorGunner on 2006-11-25
The purpose of this thread to to provide a how to on intallation of MySql Administraor 1.2.5rc  MySQL Query Browser and MySQL Workbench alpha. Personally the more GUI's for mysql the better. This Version will also fix some freeze ups that occur in the apt-get version 1.1.0

Download mysql-gui-tools-5.0r6-linux-i386.tar.gz from the mysql site. This one is for x86 you can pick what ever you need.
[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

cd /home/your_name/Desktop

To unpack the gunzip file 
Desktop$ sudo tar --directory=/opt -xzvf mysql-gui-tools-5.0r6-linux-i386.tar.gz

Move the following desktop files so they will show up in your development area of your K-menu or G-menu

sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop

sudo mv /opt/mysql-gui-tools-5.0/MySQLQueryBrowser.desktop /usr/share/applications/MySQLQueryBrowser.desktop

sudo mv /opt/mysql-gui-tools-5.0/MySQLWorkbench.desktop /usr/share/applications/MySQLWorkbench.desktop

Open the MySQL admin file
sudo gedit /usr/share/applications/MySQLAdministrator.desktop
Edit 
Categories=GTK;Database;Development;Applications
to say
Categories=GTK;Database;Development
This will ensure all of the start icons are in the same place

Edited 09 Dec 06 as per Olav's correction

---

### Post by Olav on 2006-12-06
That actually worked, after I gave up on Workbench a couple of months ago I am now Workbenchin'! 8) 

Still one little thing though. Following the above method I would get this error on starting MySQL Workbench: "The GRT environment for the Workbench could not be initialized. Please verify your installation. "

A quick and dirty fix is to edit the file /opt/mysql-gui-tools-5.0/mysql-workbench and replace the last line

```
$PRG-bin $args
```

with this:

```
LANG=C $PRG-bin $args
```

**Slight edit:** In the above post by DoorGunner, replace this

```
sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop
sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop
sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop
```

with this:

```
sudo mv /opt/mysql-gui-tools-5.0/MySQLAdministrator.desktop /usr/share/applications/MySQLAdministrator.desktop
sudo mv /opt/mysql-gui-tools-5.0/MySQLQueryBrowser.desktop /usr/share/applications/MySQLQueryBrowser.desktop
sudo mv /opt/mysql-gui-tools-5.0/MySQLWorkbench.desktop /usr/share/applications/MySQLWorkbench.desktop
```

Just in case someone was wondering! :)

---

### Post by DoorGunner on 2006-12-09
DOH ](*,) should have seen that....Your absolutley right.
good pick up

---

### Post by clast on 2006-12-12
The Fix for the "GRT environment" error didn't work for me.
You can try to insert this before the last line in /opt/mysql-gui-tools-5.0/mysql-workbench:
```

unset LANG
unset LC_ALL

```

---

