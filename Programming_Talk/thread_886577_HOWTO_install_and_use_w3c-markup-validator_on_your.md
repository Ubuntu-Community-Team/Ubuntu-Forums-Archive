---
title: "HOWTO: install and use w3c-markup-validator on your locally hosted website on Hardy"
date: 2008-08-11
forum: Programming Talk
---

### Post by skelooth on 2008-08-11
I'm writing this because when I installed the w3c-validator with apt-get not only did I have no idea where it installed its self, the default install paths were incorrect and private IP validation was turned off by default.

This extremely short Howto assumes you already have the prerequisite perl and apache2 running.

First install the package using your favorite package manager. I'll use apt-get
```
sudo apt-get install w3c-markup-validator
```

This installs the validator perl script as /usr/local/cgi-bin/check, installs the configuration files into /etc/w3c, and installs the template files into */usr/share/w3c-markup-validator/templates*. The problem is that the w3c validator would like to find the templates in /usr/local/validator/templates instead.

So make the corresponding directory structure:
```
sudo mkdir /usr/local/validator
```

Now make a soft link to point to the right spot:
```
ln -s /usr/share/w3c-markup-validator/templates /usr/local/validator/templates
```

After you've completed that step, the validator is accessible by pointing your web browser to [http://localhost/w3c-markup-validator](http://localhost/w3c-markup-validator)

If you need to validate websites that are being served privately on your network (as is usually the case with dev sites and internal mirrors) you can now edit the validator.conf file using your favorite file editor. I used vim.

```
sudo vim /etc/w3c/validator.conf
```

Find the line that says:
```
Allow Private IPs = no
```

and change it to:
```
Allow Private IPs = yes
```

There is no need to restart apache after this. You should now be able to validate your local websites!

Edit: I just confirmed that this problem only occurs in Hardy Heron. Gutsy and Feisty both worked fine with a default apt-get install of the package.

---

### Post by tuxxy on 2008-08-11
Nice, save me having to keep reloading W3C :)

---

### Post by botfish on 2008-10-03
Thank you. I got it working first time!

Does anyone have any ideas on how to move the validator to it's own virtual host so I can access it at [http://validator](http://validator) (I have the appropriate entry in /etc/hosts)

I've setup the virtual host just not sure what I should set as the DocumentRoot and ScriptAlias. Also the DocumentRoot directory options might need changing?

My validator VirtualHost container:

<VirtualHost *>
	ServerAdmin webmaster@localhost
        ServerName validator 
        ServerAlias validator.local
	
	DocumentRoot /var/www/validator/htdocs
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/validator/htdocs/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /var/www/validator/cgi-bin/
	<Directory "/var/www/validator/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/www/validator/logs/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/www/validator/logs/access.log combined
	ServerSignature On

</VirtualHost>

---

### Post by skelooth on 2008-10-10
I'm sorry I didn't see your post sooner. It should be as easy as putting

<VirtualHost *:80>
        DocumentRoot /var/www/path/to/validator
        ServerName validator
</VirtualHost>

in /etc/apache2/httpd.conf

then restarting apache

---

