---
title: "Advance Apache2 configuration on LAMP for virtual host"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by daitenshiRen on 2012-03-04
HI guys iI'm new to using Ubuntu and is usung Ubuntu 11.10, I'm using a MAC in my work for dev web apps, and is enjoying my settings there. Now i want to use my own laptop to develop web sites. in MAMP i have configure it so that all my configuration are on /etc/hosts and a specified path to a .conf file.
in MAC the structure is as follows:
- WORKDISK folder
  - CONFIG/vhosts  <- this folder contain my custom config like a sites.conf 
  - php Framework <- well a framework im using
  - www <- the project files
-my config on apache.conf
```

NameVirtualHost *
Include /Volumes/WorkDisk/CONFIG/vhosts/*.conf

```so as you can see it points out to the path the config folder

in Ubuntu i was trying to do the same but no success
i tired to comment out the: 
```
Include /sites-available
```and add:
```
Include /home/ubuntuName/WorkDisk/CONFIG/vhosts/*.conf
```can anyone point me to the right direction?

---

### Post by acc61287 on 2012-03-04
I'm using ubuntu 10.04
Install apache2, libapache2-mod-php5, mysql-server, php5-mysql, php5-imap.

After you install this package, you must:

1. create folder (your website location)

**sudo mkdir /var/www/www.mywebsite.com**

2. copy apache template for virtual hosting

**sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/www.mywebsite.com**

3. Edit /etc/apache2/sites-available/www.mywebsite.com
**sudo nano /etc/apache2/sites-available/www.mywebsite.com**

It's look like this:
-----------------------------------------------------------------
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
-----------------------------------------------------------------

Then edit:

-----------------------------------------------------------------

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
        **ServerName  [www.mywebsite.com](www.mywebsite.com)**
	DocumentRoot /var/www/**[www.mywebsite.com](www.mywebsite.com)**
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/**[www.mywebsite.com](www.mywebsite.com)**>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
-----------------------------------------------------------------
then ctrl+o (save)then ctrl+x (exit)

4. Create webpage
**sudo nano /var/www/www.mywebsite.com/index.html**
-----------------------------------------------------------------
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
-----------------------------------------------------------------
ctrl+o and ctrl+x

your can place anything there :)


5. Enable your website
**sudo a2ensite [www.mywebsite.com](www.mywebsite.com)**

6. Disable your default
**sudo a2dissite 000-default**
(*or default*)
7. Edit your /etc/hosts
**sudo nano /etc/hosts**

It look like this:
-----------------------------------------------------------------
127.0.0.1	localhost
127.0.1.1	user-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
-----------------------------------------------------------------
Now add your website
-----------------------------------------------------------------
-----------------------------------------------------------------
127.0.0.1	**[www.mywebsite.com](www.mywebsite.com)**    localhost
127.0.1.1	user-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
-----------------------------------------------------------------
ctrl+o and ctrl+x

8. Restart apache
**sudo /etc/init.d/apache2 restart**

9. Restart your network
**sudo /etc/init.d/networking restart**

10. View your website
type in your browser [www.mywebsite.com](www.mywebsite.com)
You will see

It Works!
-----------------------------------------------------------------
Maybe it could help to your problem :)

---

