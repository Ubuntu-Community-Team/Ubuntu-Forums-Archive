---
title: "wordpress /= apache"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by jschreck on 2013-08-23
Good evening,
I am a very new user to linx/ubuntu.  I am creating a wordpress blog to cover my adventures in the land of linux, as well as getting my ccna.  Right now I am able to direct dns to my server here at home, but its the defualt apache page.  I am having problems linking wordpress to apache, or what ever I am doing.  My website address is lostinside.net.  The website I am trying to follow is [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress) . 

Thank you,

jschreck

Following is the command prompt that i have currently worked with. I have uninstalled and reinstalled a few times that why there is a few commands out of order.  The following wall of text is my latest attempt.

schreck@lostinside:/var/www$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
schreck@lostinside:/var/www$ sudo gzip -d /usr/share/doc/wordpress/examples/setup-mysql.gz
gzip: /usr/share/doc/wordpress/examples/setup-mysql already exists; do you wish to overwrite (y or n)? y
schreck@lostinside:/var/www$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress lostinside.net
PING lostinside.net (24.117.22.223) 56(84) bytes of data.
64 bytes from 24-117-22-223.cpe.cableone.net (24.117.22.223): icmp_req=1 ttl=64 time=0.269 ms


--- lostinside.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.269/0.269/0.269/0.000 ms
WARNING: /etc/wordpress/config-lostinside.net.php exists!
schreck@lostinside:/var/www$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_lostinside_net wordpress.lostinside.org
ping: unknown host wordpress.lostinside.org
schreck@lostinside:/var/www$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_lostinside_net wordpress.lostinside.net
ping: unknown host wordpress.lostinside.net
schreck@lostinside:/var/www$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n wordpress_lostinside_net lostinside.net
PING lostinside.net (24.117.22.223) 56(84) bytes of data.
64 bytes from 24-117-22-223.cpe.cableone.net (24.117.22.223): icmp_req=1 ttl=64 time=0.269 ms


--- lostinside.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.269/0.269/0.269/0.000 ms
wordpress_lostinside_net is longer than MySQL's limit of 16 characters. Please specify a shorter one.
schreck@lostinside:/var/www$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n lostinside_net lostinside.net
PING lostinside.net (24.117.22.223) 56(84) bytes of data.
64 bytes from 24-117-22-223.cpe.cableone.net (24.117.22.223): icmp_req=1 ttl=64 time=0.271 ms


--- lostinside.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.271/0.271/0.271/0.000 ms
WARNING: /etc/wordpress/config-lostinside.net.php exists!
schreck@lostinside:/var/www$ sudo nano ^C
schreck@lostinside:/var/www$ cd /etc/wordpress/
schreck@lostinside:/etc/wordpress$ ls
config-localhost.php       config-lostinside.php
config-lostinside.net.php  htaccess
schreck@lostinside:/etc/wordpress$ sudo nano config-localhost.php 
schreck@lostinside:/etc/wordpress$ sudo nano config-lostinside.php
schreck@lostinside:/etc/wordpress$ sudo nano config-lostinside.net.php
schreck@lostinside:/etc/wordpress$ sudo rm -rf config-lostinside.net.php
schreck@lostinside:/etc/wordpress$ sudo rm -rf config-lostinside.php
schreck@lostinside:/etc/wordpress$ sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n lostinside_net lostinside.net
PING lostinside.net (24.117.22.223) 56(84) bytes of data.
64 bytes from 24-117-22-223.cpe.cableone.net (24.117.22.223): icmp_req=1 ttl=64 time=0.293 ms


--- lostinside.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.293/0.293/0.293/0.000 ms
/etc/wordpress/config-lostinside.net.php written
Trying to create wp-content directory: /srv/www/wp-content/lostinside.net
Setting up permissions
Goto [http://lostinside.net](http://lostinside.net) to setup Wordpress
schreck@lostinside:/etc/wordpress$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
schreck@lostinside:/etc/wordpress$ cd
schreck@lostinside:~$ sudo ln -s /etc/wordpress/config-localhost.php /etc/wordpress/config-lostinside.net.php
ln: failed to create symbolic link ‘/etc/wordpress/config-lostinside.net.php’: File exists
schreck@lostinside:~$

---

### Post by thetitan on 2013-08-24
Seems like your virtual host is not setup properly. Could you post your virtual host config for the site.

Also, did you do the manual setup or are you following the CLI instructions for installing WordPress from the repo?

I would strongly recommend just doing the manual install in the /var/www/html directory. Or whatever you have setup as the default home directory for Apache. The installation is much simpler this way.

1. Download and unzip the WordPress package into /var/www/html/lostinside/.
2. Create a virtual host for the lostinside.net and set it's directory to the above path.
3. Restart Apache.
4. Rename wp-config-sample.php to wp-config.php.
5. Update wp-config.php with your db auth credentials.
6. Navigate to lostinside.net in your browser.

Let me know if have problems with the above.

---

### Post by 2Stoned on 2013-08-24
When you tried the above (as thetitan mentioned), put the following configuration in _apache2.conf_ and _httpd.conf_ just to test if it all works.

Open the apache2 configuration with nano:
```
$ sudo nano /etc/apache2/apache2.conf
```

..and paste the following on the bottom:

```
NameVirtualHost *:80 
 
<VirtualHost *:80> 
    DocumentRoot "/var/www/html/lostinside" 
    ServerName lostinside.net 
    ServerAlias lostinside.net www.lostinside.net
    ErrorLog /var/log/apache2/lostinside-error.log 
    CustomLog /var/log/apache2/lostinside-access.log common 
</VirtualHost>
```


Open httpd.conf with nano:

```
$ sudo nano /etc/apache2/httpd.conf
```

..and paste the following to fix the servername error:

```
ServerName localhost
```

Restart apache2: ```
$ sudo service apache2 restart
```

---

