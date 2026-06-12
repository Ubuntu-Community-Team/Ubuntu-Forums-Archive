---
title: "Setting Up Virtual Host on Ubuntu 14.04"
date: 2014-09-13
forum: New to Ubuntu
---

### Post by khan3 on 2014-09-13
Hi,

I am trying to setup a virtual host on my machine.

I have created a small site which uses the Twitch API. So i have a site folder called: var/www/MyTwitch.com

Here is what i have done so far:

1. I've created a new conf file in etc/apache2/sites-available/MyTwitch.com.conf

```
<VirtualHost *:80>
    ServerAdmin admin@MyTwitch.com
    ServerName MyTwitch.com
    ServerAlias www.MyTwitch.com
    DocumentRoot /var/www/MyTwitch.com
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```


2. I've then enabled the site using 
```
sudo a2ensite MyTwitch.com.conf
```

3. Then Restart 

```
sudo service apache2 restart
```

4. I've then changed the  /etc/hosts file to:

```

127.0.0.1    localhost
127.0.1.1    ubuntu
127.0.1.1    MyTwitch.com

```

Now when i try to navigate to MyTwitch.com/index.php

It loads a blank page. Am i missing something? Also is there a way to setup multiple virtual hosts without assigning a fake domain as i like to know im working on a dev envrioment with some sort of a prefix like localhost/mytwitch.com/index.php.

Thanks.

---

### Post by khan3 on 2014-09-13
I tried pinging it, i get unknown host.

---

### Post by Lars Noodén on 2014-09-14
> **khan3 said:**
> I tried pinging it, i get unknown host.

Which did you try pinging?  There is no entry in the /etc/hosts you showed above for [www.MyTwitch.com](www.MyTwitch.com) so it will come back with an error of 'unknown host'  Try a line like this:

```

127.0.1.1    MyTwitch.com    www.MyTwitch.com

```

The file [/etc/hosts](http://manpages.ubuntu.com/manpages/trusty/en/man5/hosts.5.html) only resolves specific, individual hosts.  It's a kludge but one that works.  

As far as liking to know you are in a development environment, you can call the host anything you like since it's your hosts file.  You can give it a name that clearly identifies it as a development site, if the software is not poorly designed.  If software is poorly designed it will have hardcoded references to the full domain name, rather than figure out things based on relative paths.

---

### Post by khan3 on 2014-09-14
i tried pinging 
MyTwitch.com.

I've just switched to this in my hosts file.

127.0.0.1    localhost
127.0.1.1    ubuntu
127.0.1.1       MyTwitch.com    [www.MyTwitch.com](www.MyTwitch.com)



and i am still getting a blank page when i go to MyTwitch.com

---

### Post by khan3 on 2014-09-14
when i try to navigate the usual way..

[http://localhost/MyTwitch.com/index.php](http://localhost/MyTwitch.com/index.php)

i get

The requested URL /MyTwitch.com/index.php was not found on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80

but

just localhost works and brings back the apache success message.

---

### Post by khan3 on 2014-09-14
Ok so i created a html file in the folder. var/www/MyTwitch.com/html.index

when i navigate to that it works with a success. Just no php files are working.

---

### Post by khan3 on 2014-09-14
I know the problem, it's do with my some hardcoded references. Ty!


It was wierd how it wasent giving me the usual reference error tho.

---

