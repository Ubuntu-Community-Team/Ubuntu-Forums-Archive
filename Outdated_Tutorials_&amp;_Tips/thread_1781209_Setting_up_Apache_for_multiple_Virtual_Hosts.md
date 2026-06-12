---
title: "Setting up Apache for multiple Virtual Hosts"
date: 2011-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by ItsAsh on 2011-06-13
Hi Guys,

I have recently been looking around at peoples problems with Apache, and the most common problem I notice is multiple virtual hosts on one single server.

I will give a very simple, and thorough tutorial below, which I hope should enlighten simple problems which nobody has addressed.

Before we start i am assuming the following:

* You are running Ubuntu 11.04.
* You are installing Apache2.
* You have two domain names pointed to your DNS/IP addresses.

Now let's start off by installing Apache2.

```
sudo apt-get install apache2
```

This will install apache2 on the server inside the **/etc/apache2** directory.

And now all you want to do is have the following:

* /var/www/domain1.com/
* /var/www/domain2.com/
* and so on?

Well first of all i suggest the following:

* /var/www/domain1.com/dev/  -> Development site!
* /var/www/domain1.com/stage/ -> Staging / UAT
* /var/www/domain1.com/logs/ -> Logs from apache/php etc.
* /var/www/domain1.com/prod/ -> Live/Production site (doc root)
* /var/www/domain1.com/prod/cgi-bin/ -> CGI Dir for live site!

Now when you enter "www.domain.com" this will goto the /var/www/domain1.com/prod/ directory! you can then set-up sub-domains and HTTP authenticate them to restrict access to your development and staging environments.

Anyway, let's create our site directories.

```
sudo mkdir /var/www/domain1.com /var/www/domain1.com/dev  /var/www/domain1.com/stage  /var/www/domain1.com/prod  /var/www/domain1.com/logs
```

After the directories are created, create 2 index files (for testing purposes).

```
sudo vi /var/www/domain1.com/prod/index.htm
```

Entire some text, and save this (so you know it website 1).

Repeat this step replacing **domain1.com** to your second domain name.

Right, now we just need to get Apache to work, first I will explain the common error people are faced with,
normally an error something along the lines of "NameVirtualHost *:80 has no Virtual Hosts" this is a quick fix.

```
sudo vi /etc/apache2/ports.conf
```

And you see this line:

```
NameVirtialHosts *:80
Listen 80
```

Make this look like...

```
NameVirtualHosts *
Listen 80
```

Simply removing the ":80" from the end of that one line.

And now you need to set-up your apache config per site, using the **site-availabled** and **sites-enabled**.

first goto your sites-available and...

```
sudo cp default domain1.co.uk
```

delete the contents and replace with the following...

```
#
# /etc/apache2/sites-available/domain1.com
#
<VirtualHost *>
        ServerAdmin webmaster@example.com
        ServerName  www.domain1.com
        ServerAlias domain1.com

        # Indexes + Directory Root.
        DirectoryIndex index.html index.php
        DocumentRoot /var/www/domain1.com/prod/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/domain1.com/prod/cgi-bin
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/www/domain1.com/logs/error.log
        CustomLog /var/www/domain1.co/logs/access.log combined
</VirtualHost>
```

And save this file. Then copy this file for **domain2.com/.co.uk**

After this, you need to enable them, using symlinks, despite apache having features for this,
allow me to show you the correct way of sym linking.

```
sudo ln -s domain1.com ../sites-enabled/domain1.com
sudo ln -s domain2.com ../sites-enabled/domain2.com
```

Finally,

```
sudo /etc/init.d/apache2 restart
```

And your websites should be working correctly :).

**I understand the tutorial isn't 100% perfect, and may not thoroughly explain certain areas, however I feel the above is enough for you to understand and get multiple virtual hosts on one single server. If you have any questions or suggestions i'll be happy to answer/elaborate on them.**

I hope this helps!

---

