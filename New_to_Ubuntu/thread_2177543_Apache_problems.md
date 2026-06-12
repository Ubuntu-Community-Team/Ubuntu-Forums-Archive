---
title: "Apache problems"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by banedon on 2013-09-29
Hi guys

I've run into a bit of a problem and wondered if anyone can offer any advice.  
I'm a bit new to Apache2 and Ubuntu/Linux so if I've missed something fairly obvious please be gentle! :)

Here's the issue: I can't get my website to work - in that apache is using my IP fine, but the DNS name doesn't point to the right place/work. 

_Details_: 
I've done the following:
-Installed Ubuntu 13.04 with LAMP & SSH support
-Run packages updates & upgrades
-Given myself a static IP address which pings fine (/etc/network/interfaces)
- Set up port forwarding from my router for port 80. That's worked previously with my NAS so port 80 is not blocked by ISP.
-Added "ServerTokens Prod"  and "ServerSignature Off" to /etc/apache2/apache2.conf
-Changed "expose_php = On" to "expose_php = Off" in /etc/php5/apache2/php.ini
-*not* installed a firewall (will do that last thing - makes this test run easier to debug)
-Granted rights over the /var/www folder by adding my user account to a group and then adding that with r/w access to the /var/www folder.
```
sudo usermod -g www-data myusername
sudo chown -R www-data:www-data /var/www
sudo chmod -R 775 /var/www
```
-Added my webiste to in the usual place /var/www/mysite.com   (I've replaced my actual domain name with mysite.com for this exercise - dont' want it known until all the security is in place)
-Copied the default virtual hosts file in /etc/apache2/sites-available into the same folder, called it the name of my website (mysite.com) 
Here's a copy of the file:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName mysite.com
	ServerAlias www.mysite.com

	DocumentRoot /var/www/mysite.com
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/mysite.com>
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
</VirtualHost>
```


Now, I can get to the website by entering the server's internal IP and external IP. This gives me a file listing of the server (contains the mysite.com folder which actually contains the site)
Typing in the DNS name of the site ([http://www.mysite.com](http://www.mysite.com), [www.mysite.com](www.mysite.com), mysite.com) just has the browser sit there for a while then return a Timeout error.

This isn't a problem of mysite.com getting to my network as I have the HTTPS version of it going elsewhere and that works fine.  So I can only conclude that I've missed something with the apache server set up. Probably the Virtual Host setup somewhere..

---

### Post by The Cog on 2013-09-29
My guess is that apache is only listening on the loopback address 127.0.0.1.

Somewhere in the apache config is a line that says which address to listen on. 
The configuration you probably want is [FONT=Courier New]**listen 0.0.0.0:80**[/FONT]
which listens on all local addresses.

[http://httpd.apache.org/docs/2.2/bind.html](http://httpd.apache.org/docs/2.2/bind.html)

---

### Post by Lars Noodén on 2013-09-29
You'll want to partially undo the group permissions.  The user and group www-data exists to provide an unprivileged user for the web server.  By granting write access to either that user or group you defeat the privilege separation it would have otherwise provided.  If you instead make a new group, say "webmasters", and provide write access to that, then you'll be all right.  

About the timeout, are you sure that the DNS entry has an A record or CNAME pointing to the right ip address?  You can confirm your DNS entry by looking with [dig](http://manpages.ubuntu.com/manpages/quantal/en/man1/dig.1.html)

Also, are you behind a router / modem preventing access to the external IP?

---

### Post by banedon on 2013-09-29
@Lars Nooden
It's definitely working for my NAS (both port 80 and 443 work from the domain name).  it's only for the server (when I point the port forwarding for port 80 to it) that it fails. I've double checked the port forwarding and that looks fine (port 80 (TCP) to server internal IP)

@The Cog
I'll give that a go now and let you know.

Thanks guys :)



_Update:_
Ok, I tried your suggestion Cog, but I cannot find anyhting that mentions "Listen", "127.0.0.1", "127.0.1.1".   I'm not sure this is down to that though as the external/public IP works - just not the name.  It's almost as if it doesn't realise that my site is on the server.  I've definitely run the  sudo a2ensite mysite.com command.



_Update 2:_
I found some documentation recommending that I add the following to the virtual host file:

```
# Ensure that Apache listens on port 80
Listen 80

# Listen for virtual host requests on all IP addresses
NameVirtualHost *:80
```

This gives me a warning of :
[B][warn] NameVirtualHost *:80 has no VirtualHosts
(98)Address already in use: make_sock: could not bind to address [::]:80[/B]


_Update 3:_

I've reservsed the last changes and now I don't get the above error.  One thng which I should have mentioned previously is that when I start Apache I get the following:
**apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName**

From what I've read this isn't something t be too concerned about?


_Update 4_  (I'm a great believer in not posting 500 times in a row in seperate posts :))
I double checked mysite.com on it's own and it *does* work. Just not [www.mysite.com](www.mysite.com)
I'm not sure what I did to get that working. The virtual host file is the only thing I've chnaged and that looks the same apart from me removing some carriage returns at the top.

So I now have an alisa problem. I wonder if it's trying to find a folder called [www.mysite.com](www.mysite.com) instead to goign to the mysite.com folder... time to test!

---

### Post by banedon on 2013-09-29
Meh I think I found the problem.  I have a dynamic IP and derivatives of my DNS name registered. My synology NAS has been updating the IP for the basic DNS name (mysite.com), but not the subdomains/derivatives.
So when I use nslookup on my mysite.com it comes back with the correct IP. All others (such as [www.mysite.com](www.mysite.com)) come back with an old IP.  I was only checking mysite.com .... * facepalm*.

Serves me right for not checking the basics. :rolleyes:

Thanks for all you suggestions though! :)

---

### Post by banedon on 2013-09-29
> **Lars Noodén said:**
> You'll want to partially undo the group permissions.  The user and group www-data exists to provide an unprivileged user for the web server.  By granting write access to either that user or group you defeat the privilege separation it would have otherwise provided.  If you instead make a new group, say "webmasters", and provide write access to that, then you'll be all right.  

About the timeout, are you sure that the DNS entry has an A record or CNAME pointing to the right ip address?  You can confirm your DNS entry by looking with [dig](http://manpages.ubuntu.com/manpages/quantal/en/man1/dig.1.html)

Also, are you behind a router / modem preventing access to the external IP?

One thing to be said about this: as you might have picked up, I'm not particularly ofey when it comes to anything Linux (something I hope to correct as things progress). 
I got the those permissions settings from a guide. So it just goes to show that while someone might be well meaning, they also might be wrong.

So... just got to have a look at how permissions work with respect to apache...

---

