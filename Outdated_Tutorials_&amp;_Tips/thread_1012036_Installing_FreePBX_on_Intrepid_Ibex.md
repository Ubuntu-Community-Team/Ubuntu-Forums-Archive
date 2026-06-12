---
title: "Installing FreePBX on Intrepid Ibex"
date: 2008-12-15
forum: Outdated Tutorials &amp; Tips
---

### Post by tristangrimaux on 2008-12-15
[SIZE="6"]Installing freePBX on Ubuntu Server Intrepid[/SIZE]
[SIZE="5"]Preparing to install, things to do first[/SIZE]
Install Intrepid server as usual. Mark LAMP when installing the services. This will add Apache, MySQL and PHP5. Log in the server and access the super user account by issuing
```
sudo su
```

If you want to be sure about MySQL and PHP do this

```
apt-get install php5-mysql libapache2-mod-php5 mysql-server
```

You may need to set up apache appropriately, at the least be sure php5 is enabled. In Intrepid Ibex this is not needed:

```
a2enmod php5
```

For the localization to work properly you may have to edit /etc/php5/apache2/php.ini and modify as follow (leny/sid):

```
; PHP's built-in default is text/html
default_mimetype = "text/html"
;default_charset = "ISO-8859-1"
default_charset = "utf8";
```

Adding the last line forces the default charset for php pages (override apache charset) to be utf8.

other Php.ini settings you should change to make FreePBX happy.

```
; Magic quotes for incoming GET/POST/Cookie data.
magic_quotes_gpc = Off

;max_input_nesting_level = 64 ; Maximum input variable nesting level
memory_limit = 100M      ; Maximum amount of memory a script may consume (16MB)
```

[SIZE="5"]Install Asterisk [/SIZE]

```
apt-get install asterisk asterisk-mysql asterisk-mp3 php-db php5-gd php-pear sox curl
```

**There is no reason to install zaptel if you are using kernel 2.6 or above as it will provide the timing device unless of course you are using zaptel hardware. Ztdummy is no longer necessary.**

I am installing these also, sounds and prompts in spanish

```
apt-get install asterisk-prompt-es asterisk-sounds-extra
```

There are two approaches to solve the permissions problem, one is to add the asterisk group to the user www-data default in apache.

```
adduser www-data asterisk
```

The other one is to edit the /etc/apache2/envvars file and change apache's user to asterisk. I tested this one and it works.

```
#export APACHE_RUN_USER=www-data
#export APACHE_RUN_GROUP=www-data
export APACHE_RUN_USER=asterisk
export APACHE_RUN_GROUP=asterisk
```

Reload apache

```
apache2ctl graceful
```

To make the FOP server start, I changed the default shell for the user asterisk that was set to false:

```
usermod -s /bin/bash asterisk
```

In /usr/sbin/safe_asterisk I changed the variable BACKGROUND which is in 0 to 1

[SIZE="5"]Installing FreePBX [/SIZE]

Download freepbx from [http://www.freepbx.org](http://www.freepbx.org)

```
cd /tmp
wget http://mirror.freepbx.org/freepbx-2.5.1.tar.gz
cd /usr/src/freepbx
tar xvfz /tmp/freepbx-2.5.1.tar.gz
cd freepbx-2.5.1
```

Prepare database:

```
mysqladmin create asterisk
mysqladmin create asteriskcdrdb
mysql asterisk < SQL/newinstall.sql 
mysql asteriskcdrdb < SQL/cdr_mysql_table.sql

mysql

GRANT ALL PRIVILEGES ON asterisk.* TO asteriskuser@localhost IDENTIFIED BY 'amp109';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asteriskuser@localhost IDENTIFIED BY 'amp109';
flush privileges;
quit
```

Start installation of freepbx:

```
./install_amp
```

Here are some of the relevant settings I changed to work with ubuntu's asterisk and apache packages:

```
AMPBIN=/var/lib/asterisk/bin
ASTAGIDIR=/usr/share/asterisk/agi-bin
AMPWEBROOT=/var/www/freepbx
FOPWEBROOT=/var/www/freepbx/panel
```

In my case, after installing FreePBX Asterisk died without explanation, so after a LOT of testing I disabled two libraries that where stoping it to work. To disable a library you can add lines in /etc/asterisk/modules.conf. The autoload directive will load anything in the lib directory (/usr/lib/asterisk/modules) unless you put the line noload in the configuration file.

```
noload =>app_directory.so
noload =>res_adsi.so
```

From [http://www.voip-info.org/wiki/view/Asterisk+modules](http://www.voip-info.org/wiki/view/Asterisk+modules)
[INDENT]
app_directory.so => (Extension Directory)
res_adsi.so: Resource for ADSI applications. See [http://www.voip-info.org/wiki/view/ADSI](http://www.voip-info.org/wiki/view/ADSI)[/INDENT]

Change permissions in /usr/share/lib/asterisk

```
chown asterisk.asterisk -R /usr/share/lib/asterisk
```

To make it start at the end of everything, edit the /etc/rc.local file before the line exit 0.

```
/usr/local/sbin/amportal start
exit 0
```

note/TODO: Asterisk will start on its on after package installation. If you want to run it under safe_asterisk and managed by amportal, remove asterisk from starting on its own.

---

### Post by clarknova on 2009-02-06
Thank you for the thorough howto. I ran into a problem here:
```
# mysqladmin create asterisk
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
I know nothing about working with mysql. I checked the manpage and it suggests the command same format that you posted. Any insight?

Oh, and I'm doing this on hardy server, rather than intrepid, FWIW.

edit: one of the mysql packages prompted me to create a password when installing. Using the -p switch when creating the database has it prompt you for a password. Thus,
```
# mysqladmin -p create asterisk
Enter password:

```
seems to do the trick.

db

---

### Post by Green_Star on 2009-02-07
Does it work on Hardy Heron, Ubuntu 804?

---

### Post by clarknova on 2009-02-07
It installed fine following the directions above. If you set a root password for mysql when installing it then all your mysql commands have to include the -p flag.

It took me two tries, but after realizing that I need to accept the default password for accessing the asterisk database (amp109) it works great.

I found I had to run apache as user asterisk. adduser www-data asterisk did not work for me for some reason, kept causing an error about file permissions and agi-bin in freepbx. There's more info on this point here:
[http://freepbx.org/forum/freepbx/installation/failed-to-copy-from-module-agi-bin-0](http://freepbx.org/forum/freepbx/installation/failed-to-copy-from-module-agi-bin-0)
 
db

---

### Post by steliosv on 2009-10-20
since i was greatly helped by this post i thought i'd add that if you upgrade to asterisk 1.6 you need to create a new anything.conf file in order for freepbx (2.5.x) to work. i created the file /etc/asterisk/manager.d/admin.conf with the contents

[admin]
  secret = password
  read = system,call,log,verbose,command,agent,user,config,originate,read,write
  write = system,call,log,verbose,command,agent,user,config,originate,read,write

for googling reference this fixes the error in 

/var/log/asterisk/messages

manager.c: 127.0.0.1 tried to authenticate with nonexistent user 'admin'

and

manager.c: 127.0.0.1 failed to authenticate as 'admin'

and then this following link helped me figure the problem out.

[http://www.n3ncy.com/UNIX/Debian/Asterisk-1.6x.htm](http://www.n3ncy.com/UNIX/Debian/Asterisk-1.6x.htm)

---

### Post by steliosv on 2009-10-26
thought i'd also add that the symlink for IVR custom sounds isn't quite right if you, like me, already had a 

/usr/local/share/asterisk/sounds/

directory. just make sure the symlink is for "sounds" not "sounds/custom." or just do this.

sudo rmdir /usr/local/share/asterisk/sounds/

sudo ln -s /var/lib/asterisk/sounds/custom /usr/local/share/asterisk/sounds

i went down a wild goose chase with the agi-bin file permission errors but that doesn't seem to cause any problems. wish freepbx were a .deb which would make this all a lot easier.

---

### Post by steliosv on 2009-11-11
running into more permissions problems. amportal likes to stomp on permissions so i think it's best to make sure the ASTERISKUSER value is asterisk (and not www-data). this got my newly broken outbound trunk to work but i'm still getting the 'asterisk.ctl exist?' error when trying to run the cli which then fails. i also noticed my call logs don't have data past oct 18th which is about when i upgraded the box. i'll report what i find.

btw i'm on karmic now (as of oct 18th) with asterisk 1.6 and freepbx 2.6 so maybe this should be on a new thread.

---

### Post by steliosv on 2009-11-11
well i have cli access again and the privs aren't getting stomped on after a reboot but damn i still am not getting new data into the reports (i.e. call log). another symptom is that there aren't new entries in /var/log/asterisk/full which there are in the messages log. it's got to be a privs problem. anyone know where the call logs are stored?

---

### Post by tristangrimaux on 2009-11-11
Now I'm installing asterisk 1.6 and I'll be using your help, thanks!

---

### Post by tristangrimaux on 2010-03-06
> **steliosv said:**
> running into more permissions problems. amportal likes to stomp on permissions so i think it's best to make sure the ASTERISKUSER value is asterisk (and not www-data). this got my newly broken outbound trunk to work but i'm still getting the 'asterisk.ctl exist?' error when trying to run the cli which then fails. i also noticed my call logs don't have data past oct 18th which is about when i upgraded the box. i'll report what i find.

btw i'm on karmic now (as of oct 18th) with asterisk 1.6 and freepbx 2.6 so maybe this should be on a new thread.

I added this lines in amportal.conf

```
AMPASTERISKUSER=www-data
AMPASTERISKWEBUSER=www-data
AMPASTERISKGROUP=asterisk

```

And it worked. I did install Asterisk in a heavy use Apache installation so making it run under asterisk user was not an option.

---

