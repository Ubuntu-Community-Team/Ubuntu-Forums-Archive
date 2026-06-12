---
title: "Ubuntu + Netbeans + localhost not running"
date: 2011-01-30
forum: Programming Talk
---

### Post by todayisgood on 2011-01-30
So I installed Netbeans, but whenever I run a page the [http://localhost](http://localhost) doesn't work. I heard I need Apache to do this. Are there any step-by-step instructions I could use to do this so that Netbeans will run the localhost?

---

### Post by Zugzwang on 2011-01-30
> **todayisgood said:**
> So I installed Netbeans, but whenever I run a page the [http://localhost](http://localhost) doesn't work. I heard I need Apache to do this. Are there any step-by-step instructions I could use to do this so that Netbeans will run the localhost?

You will need to elaborate on this. Why do you think installing Netbeans will start a HTTP server process? Netbeans is an integrated development environment. If you want to use the Netbeans IDE to develop server-side programs, you will surely need to (1) start up the IDE and then (2) start some server from Netbeans. I think that you *might* refer to Tomcat development, for which, AFAIK, the server can be started from the Netbeans main window.

---

### Post by todayisgood on 2011-01-30
Sorry, I'm new to Netbeans. So how would I get the server running? I heard I should install Apache? Any instructions?

---

### Post by Zugzwang on 2011-02-01
> **todayisgood said:**
> Sorry, I'm new to Netbeans. So how would I get the server running? I heard I should install Apache? Any instructions?

As I said, you will need to explain what you are trying to do in a better way in order to get (useful) help here. At a minimum, please answer the following questions. Otherwise, we really have no clue what you mean, as there are hundreds of possibilities to what you mean right now. 

[LIST=1]
[*]Why do you think installing Netbeans will start a HTTP server process? (The answer to this question will help us in finding out what kind of server you want to start)
[*]Do you refer to tomcat programming? Possible answers are yes/no/don't know.
[*]What kind of projects do you want to develop? (The answer to this question will help us in finding out what kind of server you want to start)
[/LIST]

---

### Post by sdowney717 on 2011-02-01
you need to install apache2 and/or  LAMP
and then it needs some configuring to work. I set it up so apache2
parses files from my own folder in my user directory. I think it defaults
to parsing from a root directory somewhere.

---

### Post by sdowney717 on 2011-02-01
I set up mine as to parse from public_html
any edits you need to stop and restart apache2 server

I also added one file called etc/apache2/httpd.conf for PHP

> AddType application/x-httpd-php .php .html

from etc/apache2/sites-available/mysite file

> <VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/scott/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/scott/public_html/>
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

from etc/apache2/sites-available/default file

> <VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /home/scott/public_html
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/scott/public_html/>
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by eeperson on 2011-02-01
> **sdowney717 said:**
> you need to install apache2 and/or  LAMP
and then it needs some configuring to work. I set it up so apache2
parses files from my own folder in my user directory. I think it defaults
to parsing from a root directory somewhere.

This assumes that the user is using PHP, Python, or one of the other languages supported directly by Apache.  This may not be what the OP actually needs.  There is a good chance that the OP is doing Java development (based on the Netbeans use).  In which case the OP probably needs help setting up a Java servlet container, such as Tomcat or Jetty.

> **Zugzwang said:**
> As I said, you will need to explain what you are trying to do in a better way in order to get (useful) help here. At a minimum, please answer the following questions. Otherwise, we really have no clue what you mean, as there are hundreds of possibilities to what you mean right now. 

[LIST=1]
[*]Why do you think installing Netbeans will start a HTTP server process? (The answer to this question will help us in finding out what kind of server you want to start)
[*]Do you refer to tomcat programming? Possible answers are yes/no/don't know.
[*]What kind of projects do you want to develop? (The answer to this question will help us in finding out what kind of server you want to start)
[/LIST]

+1

---

### Post by Noobie` on 2011-05-19
Hi guys

ive got ab problem with running my php website from within netbeans. can some one help me with this please?


I just recently downloaded Netbeans 7 and apache-tomcat-7.0.14.

I set both up, i can also start and stop the server from netbeans, but when it comes to running my server site websites it gives a 404 error. this is what it says:

**HTTP Status 404 - /NCF/uciForm.php**

**type** Status report
**message** _/NCF/uciForm.php_
**description** _The requested resource (/NCF/uciForm.php) is not available._
**Apache Tomcat/7.0.14**



If you need any more details let me know please. would be great to get this running asap.


regards Noobie`

---

