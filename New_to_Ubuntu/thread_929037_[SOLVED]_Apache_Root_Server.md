---
title: "[SOLVED] Apache Root Server"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by yorkie107 on 2008-09-24
Hi a few months ago I was setting up a LAMP server and I had problems saving to the default root var/www then after days of searching I found some instructions on the web on how to change the server in apache's config but today with the help of this forum I have managed to change the ownership rights to var/www. But now I can remember how to change my root server back to the default and despite searching most of the day I can't find the web site I used to change the settings. Does anyone know what it is I type into the terminal to change it back.

Cheers

Yorkie107

---

### Post by vagena on 2008-09-24
Do you want to be a blonde one day and a redhead the next? One way to do this is to dye your own hair and restyle it, but you can achieve the same effect with much less effort &#8722; just buy [lace wig](http://www.cosprops.com/lacewigs.html). To select a wig that would be indistinguishable from real [human hair wigs](http://www.cosprops.com/lace-human-hair-wigs-c-10.html) and become your favorite fashion accessory, though, you need to know a few insider tips. First of all, if youre worried that [full lace wig](http://www.cosprops.com/lacewigs.html) will look natural on your head, never fear! A properly made wig &#8722; even the quality synthetic varieties &#8722; can look totally realistic. Which is best &#8722; synthetic or human hair wigs? Wigs can be synthetic or made from real human hair. Synthetic [front lace wig](http://www.cosprops.com/lacewigs.html) is cheaper, but the very cheap ones you can find online dont look real enough. On the other hand, high quality synthetic [cosplay wigs](http://www.cosprops.com/cosplay-wigs-c-5.html) like Revlon, Raquel Welch or Paula Young wigs look very real. Also, synthetic wigs are easier to care for, as you dont need to restyle them every time you wash them.

---

### Post by lwvmobile on 2008-09-24
The configuraion files for running servers under apache is in /etc/apache2/sites-enabled so if you look at that configuration file you will see where you point to which directory you want to host your website files.

this is what the default looks like

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
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
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

just modiligrify your DocumentRoot and Directory in the configuration file and then restart the apache2 daemon and you should be good to go.

If you need a more step-by-step answer then we will try to break it down even more for you.

:popcorn:

---

