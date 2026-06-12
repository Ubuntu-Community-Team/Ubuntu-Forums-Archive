---
title: "Installing nag2 (task manager) in dapper"
date: 2007-10-07
forum: Outdated Tutorials &amp; Tips
---

### Post by best.nose on 2007-10-07
This is an outline for installing and configuring nag2 a mulituser task manager, utilising the horde framework, from the repositories using mysql as the database backend. I have put this together because I wasted a lot of time blundering around when installing it!

This guide is from memory and aims to put some of the information together in one place to make it easier for future installers. DON'T BLAME ME IF I FORGET A STEP! The appropriate documentation, as pointed out on some web postings I googled, is included with the packages (albiet a little cryptic in some cases).

The guide follows the outline as described in the guidelines for 'Posting Your Tutorials & Tips'

It will take the following format: 

1) Credit to the base of info
2) The version of Ubuntu tested
3) Explanation of what the guide does.
4) List of what is needed to install the program
5) Uninstalling or undoing any changes made
7) Disclaimer
8) The guide itself

[SIZE="5"]**Credit for base info**[/SIZE]

Credit must be give to the authors of the documentation files:

1: The readme for configuring horde3 for debian; found at /usr/share/doc/horde3/README.Debian.gz and written by  Ola  Lundqvist (contact details in documentation) 

2: The readme for horde database installation guide; found at /usr/share/doc/horde3/examples/scripts/sql/README.gz written by people at horde (can be contacted on email address contained in documentation)

I read these files by using man (because I don't know any better), eg;

```
man <path to file>
```

You may wish to let me know if there is a more convenient way to read these files!

Credit must also be give to the people at the debian wiki for this page:

[http://wiki.debian.org/Horde](http://wiki.debian.org/Horde)


[SIZE="5"]**Version of ubuntu tested**[/SIZE]

Testing for the installation was done on Fiesty fawn, 64 bit architecture

Working installation is on Dapper 6.06LTS server edition on a 32 bit pentium 2

[SIZE="5"]**What does this guide do?**[/SIZE]

This guide aims to bring together information that I found to be dispersed across installation guides and the web for configuring components to make nag2 work on a webserver. On my system this included:
[LIST=1]
[*]Installing mysql-server
[*]Installing nag2 and dependencies (including horde and php)
[*]Initialising the mysql required database from script
[*]Placing an alias in /etc/apache2/conf.d to point to horde's config directory
[*]Updating pear and installing Mail_Mime
[*]Changing permissions on the congfig directories to allow apache to write to them
[*]Configuring horde
[*]Configuring nag2
[*]Securing the installation
[*]Problems
[/LIST]

[SIZE="5"]**What you need to install stuff (and for it to work)**[/SIZE]
[LIST]
[*]A connection to internet!
[*]Apache2
[*]The will to muck around on your system
[/LIST]

[SIZE="5"]
**Unistalling this stuff**[/SIZE]

```
sudo apt-get remove mysql-server nag2
```

That should do it.

[SIZE="5"]**Disclaimer**[/SIZE]

_I am not an it consultant - i'm a veterinarian by day! In relalion to this guide **There is no support, and the guide is to be used at your own risk.**_

Suggestions are welcome!

[SIZE="6"]The guide as follows[/SIZE]

**Installing mysql**

```
sudo apt-get install mysql-server
```

Dependencies (if any) are installed also.

Assign a root password to mysql if you haven't already (default is <blank password>):

```
mysqladmin -u root password NEWPASSWORD
```

That command only sets a password if you havn't already (i'm led to belive so anyway).

**Installing nag2**

```
sudo apt-get install nag2
```

Dependencies (if any) are installed also.

I had problems enabling php4-mysql (allowing php to interact with mysql i guess) so had to manually install this package later - so check it is in the list! php5-mysql and php5-mysqli didn't work on dapper (can't remember with fiesty as i was'just mucking around' on that machine).

Restart apache to get the appropriate modules loaded:

```
sudo /etc/init.d/apache2 restart
```

**nitialising the mysql required database from script**
Unpack the example script provided with horde installation:


```
cd /usr/share/doc/horde3/examples/scripts/sql/
sudo gunzip create.mysql.sql.gz
```

Edit create.mysql.sql so that a password only know to you is inserted rather than 'horde' in the database you are about to initialise:

```
sudo <your favourite text editor> create.mysql.sql
```

change the bit that says:

```
-- IMPORTANT: Change this password!
        PASSWORD('horde')
```

to:

```
-- IMPORTANT: Change this password!
        PASSWORD('<your_new_password')
```

Initialise the database:

```
mysql -u root -p < /usr/share/doc/horde3/examples/scripts/sql/create.mysql.sql
```

Enter your newly created (or exisiting) password for the root user of you mysql server (not the same as your adminstarotrs password you use for sudo-ing).

Initialise your nag datatable:

```
mysql -u root -p horde <   /usr/share/doc/nag2/examples/scripts/sql/nag.sql
```


**Placing an alias in /etc/apache2/conf.d to point to horde's config directory**

```
sudo <favourite test editor> /etc/apache2/conf.d/horde3
```

place the following in there:

```
Alias /horde3 /usr/share/horde3/
<Directory /usr/share/horde3>
    Options FollowSymLinks
    AllowOverride Limit
</Directory>
```

Restart apache:

```
sudo /etc/init.d/apache2 restart
```

**Updating pear and installing Mail_Mime**

Horde needs Mail_Mime and i couldn't install it with pear without first updating it:

```
sudo pear upgrade-all
sudo pear install Mail_Mime
```

**Change permissions on the congfig directories**

```
sudo chown www-data:www-data -R /etc/horde/
```

**Configure horde**

Remove exit 0 from config file (backup first):

```
sudo cp /etc/horde/horde3/config.php /etc/horde/horde3/config.php_bak
sudo <fav text ed> /etc/horde/horde3/conf.php
```

Remove these lines:

echo "Horde3 configuration disabled by default because the administration/install wizard gives the whole world too much access to the system. Read /usr/share/doc/horde3/README.Debian.gz on how to allow access.";
exit (0);

Configure horde:

First test your installation; go to 

yourservername/horde/test.php

There you shoould see no red lines (except the memory limit diasabled one - this is ok if you use sql as preferneces backend). Also mysql support support should be enabled in php settings.

I had some problems with DB not being installed in pear - if you don't have a "DB: yes" in the pear section type something like:

```
sudo pear install DB
```
 -this should do the job?!

**Configuring horde**

My configuration is pretty basic - you may wish to point out shortfalls! 

Go to yourservername/horde3

Go through the links Adminstartion > Setup > Horde3

Click the tab 'Database', select Mysql.

[LIST]
[*]Your server host is the name of your computer (or localhost)
[*]Your database username is horde
[*]Your password is the one you put in the create.mysql.sql file earlier
[*]your database is called horde
[*]Leave the other stuff at defaults
[/LIST]

Click the 'Prefernce system' tab and change the preference driver to SQL Database - leave the rest as defaults

Click the DataTree System and change to sql database - leave rest as defaults

Click 'Generate horde Configuration'

If all goes well, click Administration > Users

Add at least one user to the list (self explanatory) - remember this password!

Go back to Adminstration > Setup > horde and click the Authentication tab. Remove "Administrator" and place the username of the user (you just created in last step) that you want to have administartive priviledges.

Click 'Generate horde Configuration' - this will give you an error. Don't worry just log in (may have to logout first) as the admin user you previously created.

**Configure nag2**

On your horde homepage click Adminstartion > Setup > Tasks (nag)

Make sure the storage driver is SQL (with horde defaults as driver) and the data table is nag_tasks

Click 'Generate horde Configuration'

Make sure you can follow the link to tasks with no errors - ensure you can add a task etc.


Add users and groups to your hearts content. You can manage your startup application (sensibly tasks if you don't use other horde apps), who, of the users, sees your task lists in your horde pages. 

Useful places to start are:

Options button (both tasks options and global options). Edited on a per user basis.

MyTaskLists button (in tasks) - if you have set up a group sharing tasklists is as easy as setting up permissions for each task list!

**Securing installation**
Revert the ownership of config files to root and change the mode on files:

```
sudo chown root:www-data -R /etc/horde/
sudo chmod 0440 -R /etc/horde/
```

The file /usr/share/doc/horde3/README.Debian.gz has some other stuff to say about this, eg htaccess files in config directories. perhaps  I should?

**Problems**

On my Fiesty installation I needed a running web server with a FQDN (i used the apache2 package so this guide assumes you are too). If you do not have a FQDN for your web server you will find apache gets 'stuck' trying to authenticate your session (horde uses cookies to authenticate by default). This means the page seems to take forever to load and never does. Top would tell me apache was sucking heaps of system resource. You can change this by editing your /etc/horde/horde3/config.php file manually by changing the line that is something like:

$conf['session']['cookeis'] = true

to 'false'. The line has something about session and cookies in it - i'm not sure which one!! Take this as a warning to backup your config file before palying with it.

The dapper istallation didn't give me this problem.

Good luck - don't do anything silly to your system (i can only hope i haven't)!

---

