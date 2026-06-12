---
title: "Apache demystified: FQDN, SSL, SVN"
date: 2008-12-23
forum: Outdated Tutorials &amp; Tips
---

### Post by coolaj86 on 2008-12-23
This applies directly to Ubuntu 8.10 Intrepid Ibex

**First, let's talk about the configuration files in /etc/apache2.**

/etc/apache2/apache2.conf:
Ubuntu defaults. Don't play with this too much directly. Make minor modifications here, but store most of your customisations in httpd.conf.

/etc/apache2/httpd.conf:
An empty file. This is where you store all of your customisations. Here you should put things that are not already listed in apache2.conf.

/etc/apache2/sites-available/
Each VirtualHost *:* should have it's own ###-name.domain.tld configuration here. When you run a2dissite the configuration file stays here.

/etc/apache2/mods-available/
Each module should have it's mod-name config file here. When you run a2dismod the configuration file stays here.

/etc/apache2/sites-enabled/
Symlinks to sites that you've enabled using a2ensite ###-name.domain.tld

/etc/apache2/mods-enabled/
Symlinks to modules that you've enabled using a2enmod mod-name



Now I'm going to assume that you've got your FQDN set up through dyndns.org already, you have apache installed, and you're ready to rock and roll.

As soon as you start your server you always get this message:
**"Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName"**

There are a few things that you need to do to fix this:
httpd.conf: Add a line specifying an arbitrary primary domain name
```
ServerName mydomain.dyndns.org
```

sites-available:
Each site should have a <VirtualHost *:*> tag and inside of that you should have a ServerName which describes the virtual host.
```
ServerName mydomain.dyndns.org
```

Done! No more of that message.



**Now you probably want to get SSL up and running.**
I won't reinvent the wheel: These are great references:
[http://www.tc.umn.edu/~brams006/selfsign.html](http://www.tc.umn.edu/~brams006/selfsign.html)
[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)

You've done that and you get another error
"**Error code: ssl_error_rx_record_too_long apache**"

Try this:
[http://mydomain.dyndns.org:443](http://mydomain.dyndns.org:443)

If that works then it means that in one of your virtual hosts you neglected to add the SSLEngine ON directive
```
<VirtualHost *:443>
    #.....
    SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/server.crt
        SSLCertificateKeyFile /etc/apache2/ssl/server.key
</VirtualHost>
```


Nows lets say that you want a particular part of your site to automagically redirect to https: They enter [http://secure.mydomain.dyndns.org/paynow/](http://secure.mydomain.dyndns.org/paynow/) and you want it to detect their error:```

<VirtualHost *:80>
       ServerName secure.mydomain.dyndns.org
       Redirect seeother / https://secure.mydomain.dyndns.org/
</VirtualHost>
```


You may not like that if **doesnt-exist.mydomain.dyndns.org always points back to the real index** - or worse to the index of your primary site. To fix this you can modify the VirtualHost directive and use some php-fu (which I won't go into here) to do what you want. Make sure that each virtual host has it's own special root directory and that your default site will use /var/www/index.php to read the header of where they were going and say "did you mean to go to www.mydomain.dyndns.org?"

```
<VirtualHost *:80>
       ServerName mydomain.dyndns.org
       DocumentRoot /var/www/m/mydomain
</VirtualHost>
```

**How about getting SVN up?**
First of all, I believe that you have to do your initial import from the local machine. Or at least I didn't get it working with svn+ssh and I haven't tried an initial import from webdav.

Here's a nice howto
[http://ubuntuforums.org/showthread.php?t=51753](http://ubuntuforums.org/showthread.php?t=51753)
I also must recommend the free book on the svnbook. I printed out a few chapters and it was invaluable to my learning!
[http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

But let's say instead of having /svn show up as svn on ALL of your domains (which is the default) you want only one virtual host
[https://svn.mydomain.dyndns.tld](https://svn.mydomain.dyndns.tld)

turn svn into a site rather than a global module

```

cd /etc/apache2
rm ./mods-enabled/dav_svn.conf
mv ./mods-available/dav_svn.conf ./sites-available/###-svn.mydomain.dyndns.org

```

(This may need to be repeated when mod_dav_svn is upgraded)

and create a virtual host for it:
vim ./sites-available/###-svn.mydomain.dyndns.org
```

<VirtualHost *:443>
  ServerName svn.mydomain.dyndns.org

  <Location />
#.......
</VirtualHost>

```

And lastly you'd like to eliminate the hundred million useless errors in your log file about favicon.ico and robots.txt:
**[Mon Dec 22 18:37:16 2008] [error] [client 24.87.22.5] File does not exist: /var/www/favicon.ico**

```
cd /var/www/; wget http://help.ubuntu.com/favicon.ico
```
OR
create a 16x16 xpm in gimp and use xpm2wico to convert it
OR
use this directive in httpd.conf
```
Redirect 404 /favicon.ico
```
OR
```

  RewriteEngine On
  RewriteCond  %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f
  RewriteRule  .*favicon\.ico$         /var/www/favicon.ico [L]   
  RewriteRule  .*robots\.txt$         /var/www/robots.txt [L]
``` 




I hope this helps someone. Questions, comments welcome.

---

### Post by infallible on 2009-03-06
I'm learning all of this, and your post made a helpful synopsis. Thanks.

---

### Post by sloppyjava on 2010-01-29
Very cool post, It answered several of my questions in one fell swoop!

---

### Post by coolaj86 on 2010-02-23
I have this to say:
Nginx is 10000 times easier to configure than Apache. Why even bother with Apache? I guess there aren't as many modules for Nginx yet, but it's [super easy]("https://secure.bonkabonka.com/blog/2008/01/04/nginx_fronting_for_subversion.html") to set it up as a reverse proxy for apache + svn.

[Passenger installs Nginx for you!]("http://www.modrails.com/install.html")
[Virtual Hosts with Nginx]("http://articles.slicehost.com/2008/5/28/how-to-serve-multiple-domains")
[Nginx as a Reverse Proxy for a Thin cluster]("http://articles.slicehost.com/2008/5/27/ubuntu-hardy-nginx-rails-and-thin")
[Nginx and Passenger way easier than mod_wsgi]("http://kbeezie.com/view/using-python-nginx-passenger/2/")
[Nginx articles on Slicehost]("http://articles.slicehost.com/nginx")

---

